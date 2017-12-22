---
layout: post
title: CUDA and CuDNN Installation Tutorial - Ubuntu 16
---

## Download

You need to download CUDA and CuDNN in the main page:

+ [CUDA](https://developer.nvidia.com/cuda-downloads). You need to download a local deb file.

+ [CuDNN](https://developer.nvidia.com/cudnn)

## Install

### Install CUDA

```bash
sudo dpkg -i <file-cuda-install.dep>
sudo apt-key add  /var/cuda-repo-<version>/7fa2af80.pub
sudo apt-get update
sudo apt-get install cuda
```

The second command uses when you install CUDA version >= 9.0.

You need to add PATH and LD_LIBRARY_PATH into the os enviroment. Edit .bashrc and add 2 lines:

```bash
export PATH=$PATH:/usr/local/cuda-<version>/bin
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/usr/local/cuda-<version>/lib64 (or lib if you use 32bit)
```

Finally, you type source .bashrc and reboot your pc.

### Install CuDNN

```bash
tar -xzvf <fill-cudnn.tgz>
sudo cp cuda/include/cudnn.h /usr/local/cuda-<version>/include/
sudo cp cuda/lib64/libcudnn* /usr/local/cuda-<version>/lib64/
sudo chmod a+r /usr/local/cuda-<version>/include/cudnn.h /usr/loca/cuda-<version>/lib64/libcudnn*
```

## Notes

+ You should try to install one version CUDA on your PC. It can be conflicted between CUDA versions and NVIDIA Card Driver.

+ Before installing CUDA, you should try to purge remove NVIDIA Card Driver to avoid conflicting.

+ When you use CUDA for training, you may not login your ubuntu into desktop in next login. To deal with the problem, you login into tty and purge remove CUDA and its dependencies. After, you login into your desktop and reinstall CUDA and CuDNN.
