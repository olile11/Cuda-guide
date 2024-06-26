# Cuda-guide
Install and setup cuda and required library on ubuntu24


# 1 - Prepare the machine 
## 1.1 - Check if Your GPU is Capable of Running CUDA  
`lspci | grep -i nvidia`  
Obs: if the return in nothing or no output, then your machine not suport  
## 1.2 - Install nvidia-driver  
run this the below command to see the recommended version  
`sudo ubuntu-drivers devices`  
and them install the recommended version: for exemple "nvidia-driver-535"  
`sudo apt install nvidia-driver-535`  
or Alternatively, install it automatically  
`sudo apt auto-install`  
finally, reboot the system  

# 2 - Check the gcc version  
`gcc -version`  
if not installed, run the below command to install   
`sudo apt install gcc`  

# 3 - Installing cuda   
## 3.1 - first, update the local repository  
`sudo apt update && sudo apt upgrade`
## 3.2 - Install Cuda Toolkit on Ubuntu
`sudo apt install nvidia-cuda-toolkit`
reboot the system
## 3.3 Verify the system
`nvcc --version`

# 4 - Install CuDNN
## 4.1 - first, download the version of CuDNN
`wget https://developer.download.nvidia.com/compute/cudnn/9.1.1/local_installers/cudnn-local-repo-ubuntu2204-9.1.1_1.0-1_amd64.deb` 
Choose the preferable version  
## 4.2 - install the package
`sudo dpkg -i cudnn-local-repo-ubuntu2204-9.1.1_1.0-1_amd64.deb`
## 4.3 - copy the key to share
`sudo cp /var/cudnn-local-repo-ubuntu2204-9.1.1/cudnn-*-keyring.gpg /usr/share/keyrings/`  
## 4.4 update the repo
`sudo apt update`
## 4.5 Install cudnn or especify version
`sudo apt-get -y install cudnn` or `sudo apt-get -y install cudnn-cuda-11` cuda-11 or `sudo apt-get -y install cudnn-cuda-12` for 12
## 4.6 Test them with torch
`import torch`  
`print(torch.cuda.is_available())`  
the output should be `true`  
or with tensorflow
`import tensorflow as tf`  
`print("Num GPUs Available: ", tf.config.list_physical_devices('GPU') , len(tf.config.list_physical_devices('GPU')))`

## Ref
* [source](https://www.liberiangeek.net/2024/04/install-cuda-on-ubuntu-24-04/)

