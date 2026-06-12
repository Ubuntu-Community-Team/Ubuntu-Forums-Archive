---
title: "Driver Installation for AMD Ryzen AMD® Ryzen 7 pro 5850u on Ubuntu 20.04.3 failed"
date: 2021-09-15
forum: New to Ubuntu
---

### Post by jhamra on 2021-09-15
Dear Community

I recently bought a Thinkpad P14s Gen 2 with an AMD® Ryzen 7 pro 5850u  processor, but without an operating system. I followed the official  instruction guidelines from Lenovo to install Ubuntu 20.04. However, the  installation of the AMD Pro drivers failed with the error trace given  below. Now it seems that every time I try to install something, I get  this error message. In the "Software & Updates" app under the "Other  Software" tab  the new entry "file:/var/opt/amdgpu-pro-local/ ./" is  shown with a check mark. But, I think, the installation completely  failed. I also attached the make.log as a zip for further information.  Should I uninstall the driver first? I appreciate any help to install the  driver!

Best
Jannis

Link of the driver: [URL="http://www.amd.com/en/support/kb/release-notes/rn-amdgpu-unified-linux-20-20"]http://www.amd.com/en/support/kb/release-notes/rn-amdgpu-unified-linux-20-20
[/URL]Installation guidelines: [http://amdgpu-install.readthedocs.io/en/latest/](http://amdgpu-install.readthedocs.io/en/latest/)

Only error message:
```
Building initial module for 5.11.0-34-generic
Error! Bad return status for module build on kernel: 5.11.0-34-generic (x86_64)
Consult /var/lib/dkms/amdgpu/5.6.0.15-1098277/build/make.log for more informatio
n.
dpkg: error processing package amdgpu-dkms (--configure):
 installed amdgpu-dkms package post-installation script subprocess returned erro
r exit status 10
Setting up libglapi1-amdgpu-pro:amd64 (20.20-1098277) ...
Setting up libglapi1-amdgpu-pro:i386 (20.20-1098277) ...
Setting up libselinux1:i386 (3.0-1build2) ...
dpkg: dependency problems prevent configuration of amdgpu:
 amdgpu depends on amdgpu-dkms (= 1:5.6.0.15-1098277); however:
  Package amdgpu-dkms is not configured yet.

dpkg: error processing package amdgpu (--configure):
 dependency problems - leaving unconfigured
Setting up libgl1-amdgpu-pro-dri:amd64 (20.20-1098277) ...
No apport report written because the error message indicates its a followup erro
r from a previous failure.
                          Setting up libgl1-amdgpu-pro-dri:i386 (20.20-1098277) 
...
Setting up libgl1-amdgpu-pro-appprofiles (20.20-1098277) ...
Setting up libxfixes3:i386 (1:5.0.3-2) ...
Setting up libegl1-amdgpu-pro:amd64 (20.20-1098277) ...
Setting up libegl1-amdgpu-pro:i386 (20.20-1098277) ...
Setting up libllvm12:i386 (1:12.0.0-3ubuntu1~20.04.4) ...
Setting up libegl1-amdgpu-mesa-drivers:amd64 (1:20.0.5-1098277) ...
Setting up libgles2-amdgpu-pro:amd64 (20.20-1098277) ...
Setting up libgles2-amdgpu-pro:i386 (20.20-1098277) ...
Setting up libvdpau1:i386 (1.3-1ubuntu2) ...
Setting up libgl1-amdgpu-pro-glx:amd64 (20.20-1098277) ...
Setting up libgl1-amdgpu-pro-glx:i386 (20.20-1098277) ...
Setting up mesa-vdpau-drivers:i386 (21.0.3-0ubuntu0.3~20.04.1) ...
dpkg: dependency problems prevent configuration of amdgpu-pro:
 amdgpu-pro depends on amdgpu (= 20.20-1098277); however:
  Package amdgpu is not configured yet.

dpkg: error processing package amdgpu-pro (--configure):
 dependency problems - leaving unconfigured
Setting up libgl1-amdgpu-pro-ext:amd64 (20.20-1098277) ...
No apport report written because the error message indicates its a followup erro
r from a previous failure.
                          Setting up libglapi-amdgpu-mesa:i386 (1:20.0.5-1098277
) ...
Setting up mesa-amdgpu-vdpau-drivers:i386 (1:20.0.5-1098277) ...
Setting up amdgpu-lib (20.20-1098277) ...
dpkg: dependency problems prevent configuration of amdgpu-pro-lib32:
 amdgpu-pro-lib32 depends on amdgpu (= 20.20-1098277) | amdgpu-hwe (= 20.20-1098
277); however:
  Package amdgpu is not configured yet.
  Package amdgpu-hwe is not installed.
 amdgpu-pro-lib32 depends on amdgpu-pro (= 20.20-1098277) | amdgpu-pro-hwe (= 20
.20-1098277); however:
  Package amdgpu-pro is not configured yet.
  Package amdgpu-pro-hwe is not installed.

dpkg: error processing package amdgpu-pro-lib32 (--configure):
 dependency problems - leaving unconfigured
Setting up libgles1-amdgpu-mesa:i386 (1:20.0.5-1098277) ...
No apport report written because MaxReports is reached already
                                                              Setting up vdpau-d
river-all:i386 (1.3-1ubuntu2) ...
Setting up libegl1-amdgpu-mesa:i386 (1:20.0.5-1098277) ...
Setting up libgl1-amdgpu-mesa-glx:i386 (1:20.0.5-1098277) ...
Setting up libgles2-amdgpu-mesa:i386 (1:20.0.5-1098277) ...
Setting up libgl1-amdgpu-mesa-dri:i386 (1:20.0.5-1098277) ...
Setting up libosmesa6-amdgpu:i386 (1:20.0.5-1098277) ...
Setting up libegl1-amdgpu-mesa-drivers:i386 (1:20.0.5-1098277) ...
Setting up amdgpu-lib32 (20.20-1098277) ...
Processing triggers for systemd (245.4-4ubuntu3.11) ...
Processing triggers for man-db (2.9.1-1) ...
Processing triggers for libc-bin (2.31-0ubuntu9.2) ...
Processing triggers for initramfs-tools (0.136ubuntu6.6) ...
update-initramfs: Generating /boot/initrd.img-5.11.0-34-generic
Errors were encountered while processing:
 amdgpu-dkms
 amdgpu
 amdgpu-pro
 amdgpu-pro-lib32

```

---

### Post by zvacet on 2021-09-15
Type in terminal 

```
sudo dpkg --configure -a
```

If you still get errors, please post  output here.

---

### Post by jhamra on 2021-09-15
Unfortunately, I still get an error:

```

 sudo dpkg --configure -a
[sudo] password for jannis: 
Setting up amdgpu-dkms (1:5.6.0.15-1098277) ...
Removing old amdgpu-5.6.0.15-1098277 DKMS files...

------------------------------
Deleting module version: 5.6.0.15-1098277
completely from the DKMS tree.
------------------------------
Done.
Loading new amdgpu-5.6.0.15-1098277 DKMS files...
Building for 5.11.0-34-generic
Building for architecture x86_64
Building initial module for 5.11.0-34-generic
ERROR: Cannot create report: [Errno 17] File exists: '/var/crash/amdgpu-dkms.0.crash'
Error! Bad return status for module build on kernel: 5.11.0-34-generic (x86_64)
Consult /var/lib/dkms/amdgpu/5.6.0.15-1098277/build/make.log for more information.
dpkg: error processing package amdgpu-dkms (--configure):
 installed amdgpu-dkms package post-installation script subprocess returned error exit status 10
dpkg: dependency problems prevent configuration of amdgpu:
 amdgpu depends on amdgpu-dkms (= 1:5.6.0.15-1098277); however:
  Package amdgpu-dkms is not configured yet.

dpkg: error processing package amdgpu (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of amdgpu-pro:
 amdgpu-pro depends on amdgpu (= 20.20-1098277); however:
  Package amdgpu is not configured yet.

dpkg: error processing package amdgpu-pro (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of amdgpu-pro-lib32:
 amdgpu-pro-lib32 depends on amdgpu (= 20.20-1098277) | amdgpu-hwe (= 20.20-1098277); however:
  Package amdgpu is not configured yet.
  Package amdgpu-hwe is not installed.
 amdgpu-pro-lib32 depends on amdgpu-pro (= 20.20-1098277) | amdgpu-pro-hwe (= 20.20-1098277); however:
  Package amdgpu-pro is not configured yet.
  Package amdgpu-pro-hwe is not installed.

dpkg: error processing package amdgpu-pro-lib32 (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 amdgpu-dkms
 amdgpu
 amdgpu-pro
 amdgpu-pro-lib32


```

---

### Post by mikewhatever on 2021-09-15
Same error here: [https://askubuntu.com/questions/1287904/amd-gpu-dkms-not-building-in-kernel-5-8-5-8-xanmod](https://askubuntu.com/questions/1287904/amd-gpu-dkms-not-building-in-kernel-5-8-5-8-xanmod)

---

### Post by jhamra on 2021-09-16
The provided link by @mikewhatever does give a solution only for the standard drivers, not the pro version. 
However i found a solution for ubuntu 20.04.2, with a specific kernel and an older version of the amdgpu-pro drivers.

The combination that seems to work:

[LIST]
[*]linux-headers-5.4.0-58-generic headers work 
[*]amdgpu-pro-20.40-1147286-ubuntu-20.04 
[*]Link with clear instructions: [https://community.amd.com/t5/drivers-software/amdgpu-pro-20-45-amdgpu-dkms-fails-error-solution-for-ubuntu-20/td-p/458997](https://community.amd.com/t5/drivers-software/amdgpu-pro-20-45-amdgpu-dkms-fails-error-solution-for-ubuntu-20/td-p/458997) 
[/LIST]

Before I try this, I have some questions:

[LIST=1]
[*]Can you recommend me to use an older Ubuntu version: **From 20.04.3 to 20.04.2** 
[*]Is it save to use an older kernel? Currently I have: **5.11.0-34.36~20.04.1-generic 5.11.22** 
[*]If I downgrade my system, I am probably stuck with this specific ubuntu version. Can I still use sudo apt-get update and sudo apt-get upgrade,or will this change the kernel and ubuntu version or will this update the older version of the amdgpu-pro drivers? 
[/LIST]

Is it better to just stay with the current ubuntu version and the amd drivers that came with it? 
Everything runs quite well, however I probably won't get the max out of the performance.

---

### Post by mastablasta on 2021-09-16
i will add in red:

> **jhamra said:**
> 
Before I try this, I have some questions:

[LIST=1]
[*]Can you recommend me to use an older Ubuntu version: **From 20.04.3 to 20.04.2[COLOR=#ff0000] -- it doesn't work like that. part that changes is kernel version. 5.4 is in 20.04.1. [/COLOR]**[COLOR=#ff0000]**20.04.2 and ****20.04.3 are kernels that were in non LTS versions 20.10 and 21.04.**[/COLOR]
[*]Is it save to use an older kernel? Currently I have: **5.11.0-34.36~20.04.1-generic 5.11.22 --- [COLOR=#ff0000]yes in this case the 5.4 is older kernel that is in LTS and receives security patches. it doesn't have latest drivers in features. [/COLOR]**
[*]If I downgrade my system, I am probably stuck with this specific ubuntu version. Can I still use sudo apt-get update and sudo apt-get upgrade,or will this change the kernel and ubuntu version or will this update the older version of the amdgpu-pro drivers? **[COLOR=#ff0000]-- sudo apt-get update and sudo apt-get upgrade will just update the system not upgrade it. it would also update&upgrade any drivers added. but it won't upgrade the whole OS[/COLOR]**
[/LIST]

this depends on situation.
> 
Is it better to just stay with the current ubuntu version and the amd drivers that came with it? 
Everything runs quite well, however I probably won't get the max out of the performance.
in linux the opensource drivers are built into kernel. so newer kernel=newer drivers. but opensource drivers are not always optimal or do not yet support latest devices. so we sometimes need to install proprietary ones. in case of AMD i am not sure what the performance gain is. i know there is some for certain new chips, but there is no major gain for osme older chips. the pro drivers in this case are geared more to developers or for those with special needs. but they could come in handy if we don't have the newest kernel that support them in ubuntu yet. so we can use them to patch the old kernel with them.

for example we had a user here with gaming RX card that had to use them to even get any meaningful FPS in games. but on the other hand my kid has older version of Ryzen 5 APU and his laptop worked fully out of the box with the 5.4. kernel. no additonal AMD driver install was needed. but i did have to patch kernel with wi-fi drivers.

---

### Post by ActionParsnip on 2021-09-16
What is the output of:
```

lsb_release -a; uname -a

```
Thanks

---

### Post by jhamra on 2021-09-16
@ActionParsnip
```

lsb_release -a; uname -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 20.04.3 LTS
Release:    20.04
Codename:    focal
Linux jannis-ThinkPad-P14s-Gen-2a 5.11.0-34-generic #36~20.04.1-Ubuntu SMP Fri Aug 27 08:06:32 UTC 2021 x86_64 x86_64 x86_64 GNU/Linux

```

@mastablasta
Thank you, I think I will probably stick with my current version and the drivers that came with it for now. But I do have a LTS ubuntu version installed, haven't I?  
I am a little bit confused, because you answered me that *20.04.2 and 20.04.3 are kernels, which were in non LTS versions 20.10 and 21.04.*

---

### Post by mastablasta on 2021-09-17
you have LTS version installed with HWE kernel. more info here: [https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)


end of October 2021 new release is planned (21.10). it will have a new kernel. after some time (probably end of november or in december) you will probably get that new kernel as well to 20.04 and new point release will be made 20.04.4

i have 18.04 LTS with 5.4 hwe kernel installed.

---

