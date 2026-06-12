---
title: "Howto: Install Nvidia CUDA in Ubuntu 10.04"
date: 2010-11-19
forum: Outdated Tutorials &amp; Tips
---

### Post by ThomasArildsen on 2010-11-19
The following tutorial describes how to install Nvidia CUDA under Ubuntu 10.04. The described steps assume a freshly installed and security updated Ubuntu 10.04 - 64 bit. The setup has not been tested under the 32 bit version, but it should work. Please let us know if you experience any problems with Ubuntu 10.04 - 32 bit.

There are some problems installing and using CUDA 3.1 under Ubuntu 10.04, since that CUDA release only supports Ubuntu 9.10. Therefore, this tutorial describes installation of CUDA 3.2 RC2. The tutorial ***has not*** been updated for the final CUDA 3.2 release - please let me know if something does not work with the final CUDA 3.2 release. CUDA 3.2 can be found at [http://developer.nvidia.com/object/cuda_3_2_downloads.html]("http://developer.nvidia.com/object/cuda_3_2_downloads.html") in stead of the link below. The driver version for the final CUDA 3.2 will be different than the one stated in this tutorial.

[LIST=1]
[*]Download Nvidia driver and CUDA:
[LIST=2]
[*]Goto Nvidia's homepage [http://developer.nvidia.com/object/cuda_3_2_toolkit_rc.html#Linux]("http://developer.nvidia.com/object/cuda_3_2_toolkit_rc.html#Linux"), the Linux section.
[*]Download and store the following files in a location on your computer that you can find again:
[LIST=3]
[*]"Developer Drivers for Linux (260.40)" (64 bit).
[*]"CUDA Toolkit for Ubuntu Linux 10.04" (64 bit).
[*]"GPU Computing SDK code samples".
   Optional - this will only be used for verification of the CUDA installation at the end.
[/LIST][/LIST]
[*]First get rid of any existing drivers that will interfere with the Nvidia development driver (as suggested, e.g., here [http://ubuntuforums.org/showthread.php?p=9233555]("http://ubuntuforums.org/showthread.php?p=9233555")):
[LIST=2]
[*]Blacklist kernel modules:
   ```
gsudo gedit /etc/modprobe.d/blacklist.conf
``` 
   Add the following lines to the file: 
   ```
blacklist vga16fb
blacklist nouveau
blacklist rivafb
blacklist nvidiafb
blacklist rivatv
```
   Save and quit the editor. 
[*]Get rid of any installed Nvidia drivers:
   ```
sudo apt-get --purge remove nvidia-*
```
[/LIST]
[*]Reboot your PC.
[*]Go to a virtual terminal (we will need to shut down the X server):
   ```
CTRL+ALT+F5
```
   Some users have reported problems changing between virtual terminals in Ubuntu 10.04. If you have this problem, see the following solution [http://ubuntuforums.org/showthread.php?t=1473045]("http://ubuntuforums.org/showthread.php?t=1473045"). 
[*]Login at the terminal and run:
   ```
sudo service gdm stop
```
[*]Install Nvidia development drivers:
[LIST=2]
[*]Go to the location where you stored the downloaded Nvidia files and run:
```
sudo devdriver_3.2_linux_64_260.24.run
```
[LIST=3]
[*]Accept the license agreement.
[*]*Install NVIDIA's 32-bit compatibility OpenGL libraries?*
   Answer 'Yes' - we don't know if this is actually necessary, but it does not seem to hurt... 
[*]*Would you like to run the nvidia-xconfig utility to automatically update your X configuration file so that the NVIDIA X driver will be used when you restart X?*
   Answer 'Yes'.
[/LIST][/LIST]
[*]The driver should now be installed successfully. Now we install CUDA:
[LIST=2]
[*]Go to the location where you stored the downloaded Nvidia files and run:
   ```
sudo cudatoolkit_3.2.9_linux_64_ubuntu10.04.run
```
   [LIST=3]
[*]*Enter install path (default /usr/local/cuda, '/cuda' will be appended):*
   Press enter to select default path or choose another location - this tutorial assumes you choose the default path.
[/LIST]
[/LIST]
[*]Set up environment variables:
[LIST=2]
[*]Set PATH:
   ```
gksudo gedit /etc/environment
```
   Append the path to the CUDA binaries. Change 
   ```
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
``` 
   to
   ```
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/cuda/bin"
```
   Save and quit the editor. 
[*]Reload PATH:
   ```
source /etc/environment
``` 
[*]Set LD_LIBRARY_PATH:
   ```
gksudo gedit /etc/ld.so.conf.d/cuda.conf (creates a new file).
```
   Paste into the file: 
   ```
/usr/local/cuda/lib64
   /usr/local/cuda/lib
```
   Save and quit the editor. 
[*]Reload LD_LIBRARY_PATH:
   ```
sudo ldconfig
```
[/LIST]
[*]CUDA should now be installed and ready to run. If you wish, you can install the "GPU Computing SDK" and compile of the examples to verify that your installation works:
[LIST=2]
[*]Go to the location where you stored the downloaded Nvidia files and run:
   ```
gpucomputingsdk_3.2_linux.run
```
[LIST=3]
[*]*Enter install path (default ~/NVIDIA_GPU_Computing_SDK):*
   Press enter to select default path or choose another location - this tutorial assumes you choose the default path.
[*][I]Located CUDA at /usr/local/cuda
   If this is correct, choose the default below.
   If it is not correct, enter the correct path to CUDA[/I]
   Press enter to confirm.
[/LIST]
[*]Install compiler:
   ```
sudo apt-get install g++
```
[LIST=3]
[*]*Do you want to continue [Y/n]?*
   Press enter to install dependencies.
[/LIST]
[*]Repair broken link to libGL.so ([http://ubuntuforums.org/showthread.php?t=409438]("http://ubuntuforums.org/showthread.php?t=409438")):
   ```
sudo rm /usr/lib/libGL.so
sudo ln -s /usr/lib/libGL.so.260.24 /usr/lib/libGL.so
``` 
[*]Create link to libXmu.so:
   ```
sudo ln -s /usr/lib/libXmu.so.6 /usr/lib/libXmu.so
``` 
[*]Install libraries necessary to compile CUDA code examples:
   ```
sudo apt-get install freeglut3-dev libxi-dev
```
[LIST=3]
[*]*Do you want to continue [Y/n]?*
   Press enter to install dependencies.
[/LIST]
[*]Go to the GPU Computing SDK directory:
   ```
cd ~/NVIDIA_GPU_Computing_SDK/C
``` 
[*]Build code examples:
   ```
make
```
[/LIST]
[*]The compiled examples can now be found under ~/NVIDIA_GPU_Computing_SDK/C/bin/linux/release/
[/LIST]

---

### Post by cruis3r on 2010-11-22
Thank you for the instructions, it was very helpful.  However, a few questions remain:

I installed NVIDIA-Linux-x86_64-260.19.21.run  (instead of 260.40)   Is that OK? It was the most recent that I could find through the NVIDIA website

So at instruction (9.3)   I typed in: 
sudo ln -s /usr/lib/libGL.so.260.19.21 /usr/lib/libGL.so   (libGL.so.260.19.21 was an actual file in that folder)

instead of 
sudo ln -s /usr/lib/libGL.so.260.24 /usr/lib/libGL.so     (to stay consistent with the notation)


at (9.4), I typed the command in and received a message:

/usr/lib$   sudo ln -s /usr/lib/libXmu.so.6 /usr/lib/libXmu.so
                ln: creating symbolic link `/usr/lib/libXmu.so': File exists

Is that an error?


The reason I have these questions is because when I go to "make" these files in ~/NVIDIA_GPU_Computing_SDK/C I receive the following errors:

:~/NVIDIA_GPU_Computing_SDK/C$ make
make[1]: Entering directory `/home/cruiser/NVIDIA_GPU_Computing_SDK/C/common'
mkdir: cannot create directory `obj': Permission denied
make[1]: *** [makedirectories] Error 1
make[1]: Leaving directory `/home/cruiser/NVIDIA_GPU_Computing_SDK/C/common'
make: *** [lib/libcutil.so] Error 2

---

### Post by ThomasArildsen on 2010-11-23
> **cruis3r said:**
> 
I installed NVIDIA-Linux-x86_64-260.19.21.run  (instead of 260.40)   Is that OK? It was the most recent that I could find through the NVIDIA website

So at instruction (9.3)   I typed in: 
sudo ln -s /usr/lib/libGL.so.260.19.21 /usr/lib/libGL.so   (libGL.so.260.19.21 was an actual file in that folder)

instead of 
sudo ln -s /usr/lib/libGL.so.260.24 /usr/lib/libGL.so     (to stay consistent with the notation)


That should be OK. As I mentioned at the beginning of my original post, my description is based on CUDA 3.2 RC2 - not the final version. It seems the driver that comes with the final CUDA 3.2 is version 260.19.21 in stead of 260.24.

> **cruis3r said:**
> 
at (9.4), I typed the command in and received a message:

/usr/lib$   sudo ln -s /usr/lib/libXmu.so.6 /usr/lib/libXmu.so
                ln: creating symbolic link `/usr/lib/libXmu.so': File exists

Is that an error?


I think this is OK. The purpose of the above is to create a link to /usr/lib/libXmu.so.6 so it can be found as /usr/lib/libXmu.so as well. This could indicate that this has been fixed by an Ubuntu security update since I tested the setup. Are you using the 32 bit or 64 bit version of Ubuntu? I guess that could make a difference.

> **cruis3r said:**
> 
The reason I have these questions is because when I go to "make" these files in ~/NVIDIA_GPU_Computing_SDK/C I receive the following errors:

:~/NVIDIA_GPU_Computing_SDK/C$ make
make[1]: Entering directory `/home/cruiser/NVIDIA_GPU_Computing_SDK/C/common'
mkdir: cannot create directory `obj': Permission denied
make[1]: *** [makedirectories] Error 1
make[1]: Leaving directory `/home/cruiser/NVIDIA_GPU_Computing_SDK/C/common'
make: *** [lib/libcutil.so] Error 2

Can you please check the file permissions of ~/NVIDIA_GPU_Computing_SDK/C and subdirectories? The above error could appear if you accidentally ran the installer with superuser privileges, i.e.: ```
sudo gpucomputingsdk_3.2_linux.run
```
If this is the case, you will generally not have write permissions to the directory afterwards because it is owned by root. Please make sure you run it without 'sudo'.

---

### Post by mancubas on 2010-11-25
Many thanks for this great tutorial, I'm going to have a bash at installing 10.04 LTS tommorow.
 
Can I ask if this tutorial assumes that 10.04 is fully updated and compilers such as g++, libxi-dev,libxmu-dev etc etc are already installed... Any pointers you have referenace this would be appreciated.
 
Cheers.
ManC

---

### Post by ThomasArildsen on 2010-11-26
It is based on a default install of Ubuntu 10.04 LTS updated approximately September 23rd. I have not installed any additional packages prior to the steps of this tutorial.

---

### Post by mancubas on 2010-11-26
Excellent stuff, will go through this tutorial today and let you know how I get on.
 
Thanks.

---

### Post by ThomasArildsen on 2010-11-26
Thanks, I'll appreciate any feedback. I'm interested in seeing whether installing the final 3.2 (which I haven't had time to yet) will be any different than the release candidate I based the tutorial on.

---

### Post by mancubas on 2010-11-26
Hi,

I made it a little further than cruis3r I think, I get the following error message when compiling the SDK examples, I've highlighted what I think to be the problem, going to go and read the thread you kindly highlighted in your tutorial ([http://ubuntuforums.org/showthread.php?t=409438](http://ubuntuforums.org/showthread.php?t=409438)) as I suspect the problem lies here.

```

make -C src/SobelFilter/ 
make[1]: Entering directory `/home/user/NVIDIA_GPU_Computing_SDK/C/src/SobelFilter'
In file included from SobelFilter.cpp:22:
/usr/local/cuda/include/cuda_runtime.h:145: warning: unused parameter &#8216;flags&#8217;
In file included from SobelFilter.cpp:28:
SobelFilter_kernels.h:29: warning: deprecated conversion from string constant to &#8216;char*&#8217;
SobelFilter_kernels.h:29: warning: deprecated conversion from string constant to &#8216;char*&#8217;
SobelFilter_kernels.h:29: warning: deprecated conversion from string constant to &#8216;char*&#8217;
SobelFilter.cpp:46: warning: deprecated conversion from string constant to &#8216;char*&#8217;
**/usr/bin/ld: cannot find -lGL**
collect2: ld returned 1 exit status
make[1]: *** [../../bin/linux/release/SobelFilter] Error 1
make[1]: Leaving directory `/home/user/NVIDIA_GPU_Computing_SDK/C/src/SobelFilter'
make: *** [src/SobelFilter/Makefile.ph_build] Error 2

```I'm using: -

[B]Ubuntu 10.04 LTS 64bit (updated 26/11/10)
devdriver_3.2_linux_64_260.19.14.run  
cudatoolkit_3.2.12_linux_64_ubuntu10.04.run  
gpucomputingsdk_3.2.12_linux.run
[/B] 
Thanks for the assistance thus far ;)

ManC

-update-

Doing the below seem to do the trick, as already said the number notation of libGL.so keeps changing with dev driver which requires manual intervention and putting right as is in my case.

```

cd /usr/lib/
sudo rm libGL.so (file browser stated broken link prior to deletion)
sudo ln -s libGL.so.260.19.14 libGL.so

```So for the most part this nice tutorial seem to work well :)

Many thanks once again & I hope my v.small input has helped.

Onto the below which are current versions (26/11/10)

**devdriver_3.2_linux_64_260.19.21.run**
**cudatoolkit_3.2.16_linux_64_ubuntu10.04.run**
[B]gpucomputingsdk_3.2.16_linux.run

[/B]Wish me luck, will keep you posted on my progress...

-update-

All worked a treated again :)

Had to do the below thou: -

```

cd /usr/lib/
sudo rm libGL.so
sudo ln -s libGL.so.260.19.21 libGL.so

```Happy days

---

### Post by spaes on 2010-11-30
I followed the instructions but was still having issues compiling the samples. It was solved by compiling them using sudo for some reason (sudo make).

---

### Post by DavidG24 on 2011-01-01
Hi guys,

I just freshly installed Ubuntu 10.10 and have two GPU's being 

2 x Nvidia Gigabyte N98TSL-1GI 9800GT 1G GDDR3 HDMI

When I first installed Ubuntu I installed the Nvidia Driver to run two monitors in twinview. I was wondering if I am able to install the Cuda drivers for the spare GPU? and if so could I ask for some starting pointers?

Thanks in Advance,

David

ps - I should add (and I'm sure this is reflected in the above description) that I'm a complete Ubuntu noob so simple instructions please :-)

---

### Post by bhaskerchatterjee on 2011-01-20
Does the same driver/toolkit/installation method works for ubuntu_10.10_amd64? 
I am really having a tough time to install cuda on ubuntu_10.10_amd64. 

I have 420m gt which is capable of running cuda and indeed i am able to run cuda on it in win7/vc++2008. In Ubuntu 10.10-amd64 everything installs fine but when i run deviceQuery it gives:
CUDA Device Query (Runtime API) version (CUDART static linking)

cudaGetDeviceCount FAILED CUDA Driver and Runtime version may be mismatched.

FAILED
and on running bandwidthTest the response is :
Running on...

 Quick Mode

bandwidthTest.cu(598) : cudaSafeCall() Runtime API error : no CUDA-capable device is detected.

Any help please.

---

### Post by mancubas on 2011-01-31
Thought i'd confirm that this tutorial with newest devdriver, toolkit & sdk examples all work fine.

[B]Ubuntu 10.04 LTS 64bit (updated 29/1/11)
devdriver_3.2_linux_64_260.19.26.run  
cudatoolkit_3.2.16_linux_64_ubuntu10.04.run  
gpucomputingsdk_3.2.16_linux.run[/B]

Had to do the below however: -

```
cd /usr/lib/
sudo rm libGL.so
sudo ln -s libGL.so.260.19.26 libGL.so
```But worked a treat.

Thanks.

---

### Post by adeee on 2011-01-31
Why you guys tested these types of software in 64 bit. there are 32 bit users in the world and i think they are alive like me :P :P :P
so what about 32 bit any idea how to install it in 32 bit 10.04 ubuntu.

---

### Post by qantum251 on 2011-02-05
hi all, and thanks for the great tutorial, still one problem:
i'm using ubuntu 10.04 64 bit with cuda 3.2.16 64 and devdriver 260.19.26 on geforce 8400m gs make performs well but when running some model like nbody, here what pops up:

[B][COLOR=Red]> Windowed mode
> Simulation data stored in video memory
> Single precision floating point simulation
freeglut (./nbody):  ERROR:  Internal error <FBConfig with necessary capabilities not found> in function fgOpenWindow
X Error of failed request:  BadWindow (invalid Window parameter)
  Major opcode of failed request:  4 (X_DestroyWindow)
  Resource id in failed request:  0x0
  Serial number of failed request:  30
  Current serial number in output stream:  33[/COLOR]

[/B]Any idea? thanks in advance to any given help

devicequery runs correctly, and gives:

CUDA Device Query (Runtime API) version (CUDART static linking)

There is 1 device supporting CUDA

Device 0: "GeForce 8400M GS"
  CUDA Driver Version:                           3.20
  CUDA Runtime Version:                          3.20
  CUDA Capability Major/Minor version number:    1.1
  Total amount of global memory:                 267714560 bytes
  Multiprocessors x Cores/MP = Cores:            2 (MP) x 8 (Cores/MP) = 16 (Cores)
  Total amount of constant memory:               65536 bytes
  Total amount of shared memory per block:       16384 bytes
  Total number of registers available per block: 8192
  Warp size:                                     32
  Maximum number of threads per block:           512
  Maximum sizes of each dimension of a block:    512 x 512 x 64
  Maximum sizes of each dimension of a grid:     65535 x 65535 x 1
  Maximum memory pitch:                          2147483647 bytes
  Texture alignment:                             256 bytes
  Clock rate:                                    0.80 GHz
  Concurrent copy and execution:                 Yes
  Run time limit on kernels:                     Yes
  Integrated:                                    No
  Support host page-locked memory mapping:       Yes
  Compute mode:                                  Default (multiple host threads can use this device simultaneously)
  Concurrent kernel execution:                   No
  Device has ECC support enabled:                No
  Device is using TCC driver mode:               No

deviceQuery, CUDA Driver = CUDART, CUDA Driver Version = 3.20, CUDA Runtime Version = 3.20, NumDevs = 1, Device = GeForce 8400M GS


PASSED

---

### Post by rdroberto on 2011-02-16
Thanks for this wonderful tutorial :D, I've installed successfully in:
Ubuntu-10.04.1-desktop-i386 32 bit (downloaded yesterday)
cudatoolkit_3.2.16_linux_32_ubuntu10.04.run
devdriver_3.2_linux_32_260.19.26.run
gpucomputingsdk_3.2.16_linux.run

I have some comments for noobes like me :)
- there is a typo in step 2.1, use sudo or gksudo instead of gsudo
- in 6.1 and 7.1 and 9.1 I've used something like sudo sh file.run
- after 7.1 i did a reboot
- in 8.3 i didn't include /usr/local/cuda/lib64 that directory doesn't exists in my system
- 9.3 was not necessary for me, the correct link was there

---

### Post by wme7 on 2011-02-19
Thanks ThomasArildsen for your tutorial, excelent work man!
And thanks also to mancumbas for your contribution with the details regarding with the libGL.so link problem.
 
I finished compiling the SDK samples files with out errors using my home computer. (I'm currently using the NVIDIA drv 260.19.26 on Ubuntu Maverick 10.10 with a Quadro FX580 GPU.)

Now I plant to do the same in a Xeon server with 4 Tesla C1060, lets see how it goes with this one! ;)

---

### Post by Jem Masters on 2011-02-22
I did the sudo apt-get --purge remove nvidia-*

and I got the following Error - E: Couldn' t find package nvidia-*

any sugestions?

---

### Post by Gihan Lakmal on 2011-02-26
> **Jem Masters said:**
> I did the sudo apt-get --purge remove nvidia-*

and I got the following Error - E: Couldn' t find package nvidia-*

any sugestions?

It's not a problem dude because I have faced same problem in my Dev Driver installation but Installation process finished without any error.  :) :)

---

### Post by Gihan Lakmal on 2011-02-26
I have already successfully installed CUDA in Ubuntu 10.04 LTS - 32 Bit. But when make examples which provided by NVIDIA, it gives following error but some of examples are successfully make how can I fixed those errors.

[B]make[1]: Entering directory `/home/giha/NVIDIA_GPU_Computing_SDK/C/src/nbody'
/usr/bin/ld: cannot find -lGL
collect2: ld returned 1 exit status
make[1]: *** [../../bin/linux/release/nbody] Error 1
make[1]: Leaving directory `/home/giha/NVIDIA_GPU_Computing_SDK/C/src/nbody'
make: *** [src/nbody/Makefile.ph_build] Error 2[/B]

I have already try out following solutions but problem still occur 
[B]
1.  sudo make

2. cd /usr/lib/
sudo rm libGL.so
sudo ln -s libGL.so.260.19.21 libGL.so[/B]

---

### Post by Gihan Lakmal on 2011-02-26
> **Gihan Lakmal said:**
> I have already successfully installed CUDA in Ubuntu 10.04 LTS - 32 Bit. But when make examples which provided by NVIDIA, it gives following error but some of examples are successfully make how can I fixed those errors.

[B]make[1]: Entering directory `/home/giha/NVIDIA_GPU_Computing_SDK/C/src/nbody'
/usr/bin/ld: cannot find -lGL
collect2: ld returned 1 exit status
make[1]: *** [../../bin/linux/release/nbody] Error 1
make[1]: Leaving directory `/home/giha/NVIDIA_GPU_Computing_SDK/C/src/nbody'
make: *** [src/nbody/Makefile.ph_build] Error 2[/B]

I have already try out following solutions but problem still occur 
[B]
1.  sudo make

2. cd /usr/lib/
sudo rm libGL.so
sudo ln -s libGL.so.260.19.21 libGL.so[/B]

[SIZE=2][B]I have successfully resolved previous error.
Solution: install Dev Driver again[/B][/SIZE]

but now it gives following error any one have any idea, how to fixed it. :confused::confused:


[B]obj/release/bitonicSort.cu.o:tmpxft_000017f4_00000000-1_bitonicSort.cudafe1.cpp: (.text+0x1290): first defined here
collect2: ld returned 1 exit status
make[1]: *** [../../bin/linux/release/sortingNetworks] Error 1
make[1]: Leaving directory `/home/giha/NVIDIA_GPU_Computing_SDK/C/src/sortingNetworks'
make: *** [src/sortingNetworks/Makefile.ph_build] Error 2
[/B]

---

### Post by Luauu on 2011-03-04
sudo devdriver_3.2_linux_64_260.24.run I receive the following error sudo: dev_driver.run: command not found
I had renamed the filder to dev_driver to make it more simple.. x.x.. I hope I haven't made a mistake.
I am using ubuntu 10.10

---

### Post by Simlaconis on 2011-03-10
You have to do something like :
 ```
sudo chmod +x dev_driver.run
sudo ./dev_driver.run
```

---

### Post by kazem.manzoor on 2011-04-04
hi 
i have yet problem installation:( 

kazem@kazem-desktop:~/NVIDIA_GPU_Computing_SDK/C$ sudo makemake[1]: Entering directory `/home/kazem/NVIDIA_GPU_Computing_SDK/C/common'
make[1]: Leaving directory `/home/kazem/NVIDIA_GPU_Computing_SDK/C/common'
make[1]: Entering directory `/home/kazem/NVIDIA_GPU_Computing_SDK/C/common'
make[1]: Leaving directory `/home/kazem/NVIDIA_GPU_Computing_SDK/C/common'
make[1]: Entering directory `/home/kazem/NVIDIA_GPU_Computing_SDK/C/common'
make[1]: Leaving directory `/home/kazem/NVIDIA_GPU_Computing_SDK/C/common'
make[1]: Entering directory `/home/kazem/NVIDIA_GPU_Computing_SDK/shared'
make[1]: Leaving directory `/home/kazem/NVIDIA_GPU_Computing_SDK/shared'
make -C src/nbody/ 
make[1]: Entering directory `/home/kazem/NVIDIA_GPU_Computing_SDK/C/src/nbody'
/usr/bin/ld: cannot find -lGL
collect2: ld returned 1 exit status
make[1]: *** [../../bin/linux/release/nbody] Error 1
make[1]: Leaving directory `/home/kazem/NVIDIA_GPU_Computing_SDK/C/src/nbody'
make: *** [src/nbody/Makefile.ph_build] Error 2


other question:after setup driver my resolution is very bad and system can not detect my graphic and i do not  have x server in system.
what am i doing?

---

### Post by samiux on 2011-04-25
There is a HOWTO for installing CUDA 4.0 on Ubuntu 10.10 Desktop and Server.  It is installed by CUDA 4.0 PPA.  I think it can also applied to Ubuntu 10.04.

[Desktop]("http://samiux.blogspot.com/2011/04/howto-nvidia-cuda-40-rc-on-ubuntu-1010.html")
[Server]("http://samiux.blogspot.com/2011/04/howto-nvidia-cuda-40-rc-on-ubuntu.html")

Samiux

---

### Post by indianabones on 2011-07-12
Will the instructions follow the same patten and work on 10.10 and 11.04 Ubuntu as well?

---

### Post by indianabones on 2011-07-12
If anyone has got these instructions to work with 11.04 and cuda 4.0, do let me know. If not, could someone post another link to some instructions, haven't found any.

---

### Post by hiob on 2011-07-18
> **indianabones said:**
> If anyone has got these instructions to work with 11.04 and cuda 4.0, do let me know. If not, could someone post another link to some instructions, haven't found any.

i installed cuda 4.0 with 270.41.19 like described tutorial and it worked like a charm on my ubuntu x86 box

[B]another hint for people using different kernels:

you can build only the kernel module for different kernels via 

```
./devdriver_4.0_linux_32_270.41.19.run --kernel-name='<kernel-id-like-uname-r>' -K
```

[/B]

---

### Post by gnusci on 2011-08-09
The tutorial worked like a charm on Ubuntu 10.04 LTS

I also used the information here

[http://developer.nvidia.com/nvidia-gpu-computing-documentation](http://developer.nvidia.com/nvidia-gpu-computing-documentation)

And I downloaded the CUDA installers from here

[http://developer.nvidia.com/cuda-toolkit-40](http://developer.nvidia.com/cuda-toolkit-40)

Thanks! ThomasArildsen

---

### Post by err0r37 on 2011-08-17
At Step 8 "gksudo gedit /etc/environment" I am getting an error "Gtk-WARNING **: cannot open display"

Any ideas on how to get around this?

---

