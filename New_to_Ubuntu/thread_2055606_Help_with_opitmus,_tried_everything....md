---
title: "Help with opitmus, tried everything..."
date: 2012-09-09
forum: New to Ubuntu
---

### Post by ervine3 on 2012-09-09
Ok, So I have a Lenovo G780 Laptop with Integrated Intel 4000 HD Graphics alongside a Nvidia Geforce Gt 630m. However as I am now aware it is not easy to get the nvidia card to work. If anyone can help me take on this monster It would be much appreciated, as I cannot seem to figure it out.


**So I installed the new headers:**
uname -r
3.2.0-30-generic

**Here is my VGA list**:

~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)
01:00.0 VGA compatible controller: NVIDIA Corporation GeForce GT 630M (rev a1)

**When I try to use bbswitch**:
~$ tee /proc/acpi/bbswitch <<<OFF
tee: /proc/acpi/bbswitch: No such file or directory
OFF

**I can run glxgears WITHOUT optirun however when I run it with:**
~$ optirun glxgears
[ 2110.741840] [ERROR]Cannot access secondary GPU - error: [XORG] (EE) NVIDIA(0): Failed to initialize the NVIDIA GPU at PCI:1:0:0.  Please

[ 2110.741922] [ERROR]Aborting because fallback start is disabled.

[B]Important Bits of the Kernel Log:
[/B]
kernel: [ 2108.024127] NVRM: failed to copy vbios to system memory.
kernel: [ 2108.026780] NVRM: RmInitAdapter failed! (0x30:0xffffffff:861)
kernel: [ 2108.026787] NVRM: rm_init_adapter(0) failed

Any Ideas or Direction is appreciated. Thanks.

---

### Post by jaithehulk on 2012-09-10
If you can.. install the kernel 3.5 and above.
This will definitely help resolve the optimus issue.

---

### Post by ervine3 on 2012-09-10
ok So I installed the 3.5 kernal however both my ethernet and wlan got nuked in the process, which is sad.... because I cant do anything with them, I rolled back to 3.2.
I did do a manual upgrade though I don't know if that matters. (downloaded the 3.5all.deb headers and such and then ran sudo dpkg -i ./linux*.deb in the downloads folder)

If you have a better way to do it (ppa or some such magic)or some way to get my internet back (wlan) let me know. 

As for the models of my cards, they are:

Atheros AR8162/8166/8168 PCI-E Fast Ethernet Controller
Atheros AR9285 Wireless Network Adapter

Thanks!

---

### Post by jaithehulk on 2012-09-10
So currently u have kernel 3.2? and on this kernel is your ethernet and Wlan currently working?
If yes.. then for Optimus try installing bumblebee.. but I am not sure if it supports 630m..

---

### Post by jaithehulk on 2012-09-10
ok bumblebee does support 630m... but u need to run the command everytime an app shld utilize the graphics card.
So your desktop environment cant utilize the graphics card.

---

### Post by ervine3 on 2012-09-10
**I have tried bumblebee repeatedly but here is the output.**

~$ sudo apt-get install bumblebee bumblebee-nvidia 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  bumblebee bumblebee-nvidia
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/57.1 kB of archives.
After this operation, 221 kB of additional disk space will be used.
Selecting previously unselected package bumblebee.
(Reading database ... 178172 files and directories currently installed.)
Unpacking bumblebee (from .../bumblebee_3.0.1-3~preciseppa1_amd64.deb) ...
Selecting previously unselected package bumblebee-nvidia.
Unpacking bumblebee-nvidia (from .../bumblebee-nvidia_3.0.1-3~preciseppa1_amd64.deb) ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
Setting up bumblebee (3.0.1-3~preciseppa1) ...
Adding members from group(s) 'adm sudo admin' to 'bumblebee':
myname
Adding user myname to group bumblebee
update-initramfs: deferring update (trigger activated)
bumblebeed start/running, process 8420
Setting up bumblebee-nvidia (3.0.1-3~preciseppa1) ...
update-alternatives: using /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in manual mode.
update-alternatives: using /usr/lib/i386-linux-gnu/mesa/ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in manual mode.
bumblebeed stop/waiting
bumblebeed start/running, process 8472
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.2.0-30-generic
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place


**Then I check to see if bumblebeed is running**

~$ sudo service bumblebeed status
bumblebeed start/running, process 1009

**Run glxgspheres on INtel HD:**
$ glxspheres 
Polygons in scene: 62464
Visual ID of window: 0x97
Context is Direct
OpenGL Renderer: Mesa DRI Intel(R) Ivybridge Mobile 
60.275814 frames/sec - 67.267809 Mpixels/sec
60.098925 frames/sec - 67.070401 Mpixels/sec

**Run optirun glxspheres:**

~$ sudo optirun glxspheres 
[  178.734702] [ERROR]Cannot access secondary GPU - error: [XORG] (EE) NVIDIA(0): Failed to initialize the NVIDIA GPU at PCI:1:0:0.  Please

[  178.734754] [ERROR]Aborting because fallback start is disabled.

**As you can see it fails...**

**Here it is in verbose:**
~$ sudo optirun -vv glxspheres
[  266.537184] [DEBUG]Reading file: /etc/bumblebee/bumblebee.conf
[  266.666951] [DEBUG]optirun version 3.0.1 starting...
[  266.667028] [DEBUG]Active configuration:
[  266.667068] [DEBUG] bumblebeed config file: /etc/bumblebee/bumblebee.conf
[  266.667109] [DEBUG] X display: :8
[  266.667183] [DEBUG] LD_LIBRARY_PATH: /usr/lib/nvidia-current:/usr/lib32/nvidia-current
[  266.667248] [DEBUG] Socket path: /var/run/bumblebee.socket
[  266.667315] [DEBUG] VGL Compression: proxy
[  266.795294] [INFO]Response: No - error: [XORG] (EE) NVIDIA(0): Failed to initialize the NVIDIA GPU at PCI:1:0:0.  Please

[  266.795346] [ERROR]Cannot access secondary GPU - error: [XORG] (EE) NVIDIA(0): Failed to initialize the NVIDIA GPU at PCI:1:0:0.  Please

[  266.795351] [DEBUG]Socket closed.
[  266.795366] [ERROR]Aborting because fallback start is disabled.
[  266.795370] [DEBUG]Killing all remaining processes.

**I have no clue why other than the last three lines of the kern.log**

Sep 10 09:11:25 Gafgarion kernel: [  266.735294] NVRM: failed to copy vbios to system memory.
Sep 10 09:11:25 Gafgarion kernel: [  266.737977] NVRM: RmInitAdapter failed! (0x30:0xffffffff:861)
Sep 10 09:11:25 Gafgarion kernel: [  266.737984] NVRM: rm_init_adapter(0) failed

**Anyways still stumped, Thanks!**

---

### Post by ervine3 on 2012-09-10
**Also here is my bumblebee.conf:**


~$ cat /etc/bumblebee/bumblebee.conf 
# Configuration file for Bumblebee. Values should **not** be put between quotes

## Server options. Any change made in this section will need a server restart
# to take effect.
[bumblebeed]
# The secondary Xorg server DISPLAY number
VirtualDisplay=:8
# Should the unused Xorg server be kept running? Set this to true if waiting
# for X to be ready is too long and don't need power management at all.
KeepUnusedXServer=false
# The name of the Bumbleblee server group name (GID name)
ServerGroup=bumblebee
# Card power state at exit. Set to false if the card shoud be ON when Bumblebee
# server exits.
TurnCardOffAtExit=false
# The default behavior of '-f' option on optirun. If set to "true", '-f' will
# be ignored.
NoEcoModeOverride=false
# The Driver used by Bumblebee server. If this value is not set (or empty),
# auto-detection is performed. The available drivers are nvidia and nouveau
# (See also the driver-specific sections below)
Driver=nvidia

## Client options. Will take effect on the next optirun executed.
[optirun]
# The method used for VirtualGL to transport frames between X servers.
# Possible values are proxy, jpeg, rgb, xv and yuv.
VGLTransport=proxy
# Should the program run under optirun even if Bumblebee server or nvidia card
# is not available?
AllowFallbackToIGC=false


# Driver-specific settings are grouped under [driver-NAME]. The sections are
# parsed if the Driver setting in [bumblebeed] is set to NAME (or if auto-
# detection resolves to NAME).
# PMMethod: method to use for saving power by disabling the nvidia card, valid
# values are: auto - automatically detect which PM method to use
#         bbswitch - new in BB 3, recommended if available
#       switcheroo - vga_switcheroo method, use at your own risk
#             none - disable PM completely
# [https://github.com/Bumblebee-Project/Bumblebee/wiki/Comparison-of-PM-methods](https://github.com/Bumblebee-Project/Bumblebee/wiki/Comparison-of-PM-methods)

## Section with nvidia driver specific options, only parsed if Driver=nvidia
[driver-nvidia]
# Module name to load, defaults to Driver if empty or unset
KernelDriver=nvidia
Module=nvidia
PMMethod=auto
# colon-separated path to the nvidia libraries
LibraryPath=/usr/lib/nvidia-current:/usr/lib32/nvidia-current
# comma-separated path of the directory containing nvidia_drv.so and the
# default Xorg modules path
XorgModulePath=/usr/lib/nvidia-current/xorg,/usr/lib/xorg/modules
XorgConfFile=/etc/bumblebee/xorg.conf.nvidia

## Section with nouveau driver specific options, only parsed if Driver=nouveau
[driver-nouveau]
KernelDriver=nouveau
PMMethod=auto
XorgConfFile=/etc/bumblebee/xorg.conf.nouveau

---

