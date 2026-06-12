---
title: "Installing CUDA in Ubuntu 8.04"
date: 2009-03-31
forum: Outdated Tutorials &amp; Tips
---

### Post by obenauer on 2009-03-31
I recently installed Nvidia's CUDA programming environment and software development kit for doing general purpose computing on their graphics cards.  I installed it on a base Ubuntu 8.04 (Hardy Heron) system, 32-bit version.  They don't have a download package for later versions of Ubuntu (as of March 2009).  In case it benefits other people, here are the steps I followed:

1. First, I went to this URL:

[http://www.nvidia.com/object/cuda_get.html](http://www.nvidia.com/object/cuda_get.html)

I selected my operating system (Linux 32-bit), Linux version (Ubuntu 8.04), and downloaded the CUDA 2.1 driver, toolkit, and software development kit (SDK).  These are their filenames:

NVIDIA-Linux-x86-180.06-pkg1.run
cuda-linux-rel-nightly-2.1.1635-3065709.run
cuda-sdk-linux-2.10.1126.1520-3141441.run

(The numbers in the filenames may be different as they make updates.)

2. In order to change the Nvidia driver to one that supports the most recent CUDA features, I needed to exit X windows:

sudo /etc/init.d/gdm stop

(Or if you're using KDM, substitute "kdm" instead of "gdm" in the command.)

3. I hit Ctrl-Alt-F1 to start a terminal session, and logged in.

4. I removed the Nvidia driver and related files that came with the default Ubuntu installation:

sudo apt-get remove nvidia-glx-new nvidia-kernel-common ubuntu-restricted-extras linux-restricted-modules-2.6.24-19-generic linux-restricted-modules-2.6.24-22-generic linux-restricted-modules-2.6.24-23-generic linux-restricted-modules-generic

5. Install development tools:

sudo apt-get install build-essential libglut3-dev

6. I navigated to the Nvidia CUDA driver setup file that I had downloaded above (cd projects/cuda/installation in my case), and ran the command:

sudo sh NVIDIA-Linux-x86-180.06-pkg1.run

At this stage, the file /usr/lib/libcuda.so should exist.

7. I disabled the default "nv" driver:

sudo vi /etc/default/linux-restricted-modules-common
Edit DISABLED_MODULES="" to say DISABLED_MODULES="nv"

8. I rebooted the computer:

sudo reboot

Upon restarting, X windows started successfully and was using the new Nvidia driver.  (Usually this is visible because the screen resolution is higher than with the open source "nv" driver.)

9. I installed the CUDA toolkit:

sudo sh cuda-linux-rel-nightly-2.1.1635-3065709.run

This installs CUDA in the default path, /usr/local/cuda.  To uninstall it, delete this directory (rm -rf /usr/local/cuda).

10. I added CUDA directories to the default path and library path system variables, by adding these lines to ~/.bashrc:

# CUDA
export PATH=$PATH:/usr/local/cuda/bin
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/usr/local/cuda/lib

The terminal needs to be restarted for the change to take effect.

11. I installed the CUDA SDK:

sh cuda-sdk-linux-2.10.1126.1520-3141441.run

This installs the SDK to ~/NVIDIA_CUDA_SDK.

To try out the installation, I compiled the program "fluidsGL" that comes with the SDK.  First I needed some libraries it depends on:

sudo apt-get install libxi-dev libxmu-dev

12. All the example programs can then be compiled by typing "make" in the ~/NVIDIA_CUDA_SDK directory.  To run the programs, navigate to ~/NVIDIA_CUDA_SDK/bin/linux/release, and type their filenames with the location "./" as a prefix.  I ran fluidsGL ("./fluidsGL"), and it opened a window showing a green fluid.  Pointing and dragging the mouse makes the fluid move.  The other programs in the SDK also compiled and ran successfully.

---

### Post by rory526 on 2010-02-11
Thank you very much. very clear and detailed.

---

