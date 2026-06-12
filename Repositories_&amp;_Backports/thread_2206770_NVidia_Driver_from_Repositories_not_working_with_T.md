---
title: "NVidia Driver from Repositories not working with Tesla GPU on Ubuntu Server"
date: 2014-02-20
forum: Repositories &amp; Backports
---

### Post by rflyerly on 2014-02-20
Hi all,

I've got a server running Ubuntu Server 12.04 LTS that has an NVidia Tesla C2075 GPU.  I'm trying to test the device to make sure it is usable by applications, but the driver is not working properly.  I know that the device is at least visible over PCIe, because it shows up when I query the system:

$ lspci

...(other devices)...
61:00.0 VGA compatible controller: NVIDIA Corporation GF110GL [Tesla C2050 / C2075] (rev a1)

However, when using NVidia's System Management Interface [1] that was packaged with the driver from the repositories, I get the following error:

$ nvidia-smi -a

NVIDIA-SMI has failed because it couldn't communicate with NVIDIA driver. Make sure that latest NVIDIA driver is installed and running.

I've tried using both nvidia-current & nvidia-331, but neither driver works.  I don't want to use the installation script from NVidia that comes prepackaged with a driver because it causes weird page map errors, and eventually kernel panics (it probably does something nasty in kernel space).  Am I doing something wrong/do I need to install other package(s) to get the driver to work with a Tesla C2075?  Has anybody else had problems with the driver from NVidia (not the Ubuntu repos) causing kernel panics?  Thanks!

[1] [https://developer.nvidia.com/nvidia-system-management-interface](https://developer.nvidia.com/nvidia-system-management-interface)

---

