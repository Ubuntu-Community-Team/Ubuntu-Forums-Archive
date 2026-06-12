---
title: "intel HD graphics driver not working"
date: 2012-10-22
forum: New to Ubuntu
---

### Post by pratikvasa on 2012-10-22
I have a dell XPS 15 with a nvidia optimus 540m card.
first I had installed ubuntu 11.04 and the intel graphics were working fine but after upgrading to 12.04 there were no graphics driver. so I tried to install the nvidia drivers by various methods, but did not succeed. After installing the nvidia drivers my screen resolution would not go above 680X480.
 
So then I tried to install the nvidia graphics using bumblebee using the following commands.

```
sudo apt-get purge nvidia*
sudo apt-get purge nouveau*
sudo apt-get purge bumblebee*
sudo rm /etc/X11/xorg.conf
sudo apt-get install --reinstall xserver-xorg-core libgl1-mesa-glx:i386 libgl1-mesa-dri:i386 libgl1-mesa-glx:amd64 libgl1-mesa-dri:amd64 
sudo dpkg-reconfigure xserver-xorg
```

reboot

```
sudo apt-get install nvidia-current
sudo apt-get install bumblebee bumblebee-nvidia
```

reboot

after this in settings it still does not show any graphics driver installed.

I also changed the bumblebee configuration file (/etc/bumblebee/bumblebee.conf) as follows

Driver=
changed to
Driver=nvidia

further down:
## Section with nvidia driver specific options, only parsed if Driver=nvidia
[driver-nvidia]
# Module name to load, defaults to Driver if empty or unset
KernelDriver=nvidia-current ------> **Changed to KernelDriver=nvidia**
Module=nvidia
PMMethod=auto

bumblebee seems to work properly, ie

when I run 

```
optirun glxspheres
```

it works

but when i just run 

```
glxspheres
```

it gives an error

```
Polygons in scene: 62464
ERROR (593): Could not obtain RGB visual with requested properties
```


also after doing this should there be a /etc/X11/xorg.conf file on my system?? (it is not created)
what should I do??

---

### Post by NikTh on 2012-10-22
Hi , 

give the results of 

```
dpkg -l | grep -i nvidia 
cat /var/log/Xorg.0.log 
lspci -nnk | grep -iA2 vga
```As for the xorg.conf file , it is not necessary . Lot of people  consider this file as deprecated is these days and also the [bubmlebee troubleshooting page](https://github.com/Bumblebee-Project/Bumblebee/wiki/Troubleshooting) advise users to remove this file if exists.

Thanks

---

### Post by pratikvasa on 2012-10-22
ok thanks...
here is the output

```
dpkg -l | grep -i nvidia 
ii  bbswitch-dkms                          0.4.2-2~preciseppa1                          Interface for toggling the power on nVidia Optimus video cards
ii  bumblebee                              3.0.1-3~preciseppa1                          nVidia Optimus support
ii  bumblebee-nvidia                       3.0.1-3~preciseppa1                          nVidia Optimus support using the proprietary NVIDIA driver
rc  libnvtt2                               2.0.8-1+dfsg-2                               NVIDIA Texture Tools
ii  nvidia-current                         304.60-0ubuntu1~precise~xup2                 NVIDIA binary Xorg driver, kernel module and VDPAU library
ii  nvidia-settings                        304.60-0ubuntu1~precise~xup2                 Tool of configuring the NVIDIA graphics driver

```


```
lspci -nnk | grep -iA2 vga
00:02.0 VGA compatible controller [0300]: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller [8086:0116] (rev 09)
	Subsystem: Dell Device [1028:04b6]
	Kernel driver in use: i915
--
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GF108 [GeForce GT 540M] [10de:0df5] (rev ff)
03:00.0 Network controller [0280]: Intel Corporation Centrino Wireless-N 1030 [8086:008a] (rev 34)
	Subsystem: Intel Corporation Centrino Wireless-N 1030 BGN [8086:5325]

```

and the log file is quite big..so am uploading it..

---

### Post by NikTh on 2012-10-23
[quote="Xorg.0.log"]```
[    26.690] (EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
```[/quote]

Try this 
```
echo 'blacklist nouveau' | sudo tee -a /etc/modprobe.d/blacklist.conf 
echo 'nvidia' | sudo tee -a /etc/modules 
sudo rm /etc/X11/xorg.conf
``` 

and reboot your system. 

Check again with 
```
/usr/lib/nux/unity_support_test -p 
optirun nvidia-settings -c :8
```

Thanks

---

### Post by pratikvasa on 2012-10-23
Thanks for your reply..

I did what you said..

here is the output

```
/usr/lib/nux/unity_support_test -p 
Error: GLX is not available on the system

```

and for optirun nvidia-settings -c :8
It opened a window.. I have attached a screenshot for the same..

Also if possible can you please tell me what you did..as i am new to linux and trying to learn the same..

---

### Post by pratikvasa on 2012-10-23
Hey also one more thing..
when I go to additional drivers at first it never used to show anything, now it shows

nvidia-current
NVIDIA binary XORG driver, kernal module and VDPAU library
Experimental NVIDIA binary XORG driver, kernal module and VDPAU library
Experimental NVIDIA binary XORG driver, kernal module and VDPAU library

and it says nvidia-current is active but not in use,
while others are not active

And the system>details still shows nothing in graphics..

---

### Post by NikTh on 2012-10-23
We added the nouveau to blacklist . Nouveau is the open source driver (pre-installed) for Nvidia cards and we forced the system to load the nvidia (driver). 

The nvidia-settings is good that worked , but unity support test ... hmm not good. 

Do you mind to downgrade the Nvidia driver to the Original shipped with Ubuntu 12.04 ? 
Execute these commands to terminal to downgrade .
```
sudo apt-get install ppa-purge 
sudo ppa-purge ppa:ubuntu-x-swat/x-updates
sudo apt-get update 
sudo apt-get dist-upgrade
```and reboot your system again. 

Test again with above commands. 

Thanks

---

### Post by pratikvasa on 2012-10-23
I tried what you said..

after downgrading the upgrade manager showed 7 updates. I dont need to upgrade them right??

also distribution upgrade gave me this error

```
sudo apt-get dist-uprgade
[sudo] password for p: 
E: Invalid operation dist-uprgade

```

and for the commands this was the result..(Do I need to blacklist nouveau again???)


```
/usr/lib/nux/unity_support_test -p
Error: GLX is not available on the system
```

and again the nvidia card is recognised but while executing the second command it gives this error

```
optirun nvidia-settings -c :8

ERROR: Error parsing configuration file '/home/pratik/.nvidia-settings-rc' on
       line 34: 'pratik-Dell-System-XPS-L502X:8.0/FXAA=0' (Unrecognized
       attribute name).


```

and opens the window normally.

---

### Post by NikTh on 2012-10-23
No , you don't need to blacklist again. The command is ```
sudo apt-get dist-upgrade
```. Edited in above post. 

The nvidia drivers seems to work well. The issue here is the intel driver. 
Try to purge bumblebee again and reinstall it . 

```
sudo apt-get remove --purge bumblebee* 
sudo rm /etc/bumblebee/bumblebee.conf
```Then reinstall GLX 
```
sudo apt-get install --reinstall libgl1-mesa-glx
```and reinstall bumblebee 
```
sudo apt-get install bumblebee bumblebee-nvidia
```Re-installation of bumblebee will generate a new /bumblebee.conf file. 

Reboot one more time. 

Test again. 

Thanks

---

### Post by pratikvasa on 2012-10-23
hey tried all of it..but the glx is still not installed properly i guess.

```
/usr/lib/nux/unity_support_test -pError: GLX is not available on the system

```

:(

---

### Post by NikTh on 2012-10-23
Run 
```
sudo apt-get update 
sudo apt-get dist-upgrade 
sudo dpkg --configure -a
```Give the results 
```
apt-cache policy libgl1-mesa-glx
echo $DESKTOP_SESSION
```**EDIT: **

also give the results of 
```
cat /etc/bumblebee/bumblebee.conf
optirun -vv
optirun /usr/lib/nux/unity_support_test -p
```**EDIT 2: **
We struggle a problem **[SIZE=3][that is a bug]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/987949")[/SIZE]**. It is difficult to solve a bug. We try to find a workaround that will help you to use the Intel card where is more power-saving.
Thanks

---

### Post by pratikvasa on 2012-10-23
ok

here is the output

```
 apt-cache policy libgl1-mesa-glx
libgl1-mesa-glx:
  Installed: 8.0.4-0ubuntu0.1
  Candidate: 8.0.4-0ubuntu0.1
  Version table:
 *** 8.0.4-0ubuntu0.1 0
        500 http://in.archive.ubuntu.com/ubuntu/ precise-updates/main i386 Packages
        100 /var/lib/dpkg/status
     8.0.2-0ubuntu3 0
        500 http://in.archive.ubuntu.com/ubuntu/ precise/main i386 Packages

```

```
 echo $DESKTOP_SESSION
ubuntu-2d

```

```
cat /etc/bumblebee/bumblebee.conf
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
Driver=

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
# https://github.com/Bumblebee-Project/Bumblebee/wiki/Comparison-of-PM-methods

## Section with nvidia driver specific options, only parsed if Driver=nvidia
[driver-nvidia]
# Module name to load, defaults to Driver if empty or unset
KernelDriver=nvidia-current
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

```

```
 optirun -vv
[  408.199554] [DEBUG]Reading file: /etc/bumblebee/bumblebee.conf
[  408.315444] [DEBUG]optirun version 3.0.1 starting...
[  408.315533] [DEBUG]Active configuration:
[  408.315570] [DEBUG] bumblebeed config file: /etc/bumblebee/bumblebee.conf
[  408.315639] [DEBUG] X display: :8
[  408.315694] [DEBUG] LD_LIBRARY_PATH: /usr/lib/nvidia-current:/usr/lib32/nvidia-current
[  408.315731] [DEBUG] Socket path: /var/run/bumblebee.socket
[  408.315779] [DEBUG] VGL Compression: proxy
[  408.315826] [ERROR]Missing argument: application to run
Try `optirun --help' for more information.

```

```
 optirun /usr/lib/nux/unity_support_test -p
OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce GT 525M/PCIe/SSE2
OpenGL version string:  4.2.0 NVIDIA 295.40

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  no
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       no

```

hey i did not understand the link that you sent..can you please elaborate..thanks

---

### Post by NikTh on 2012-10-23
Open the /etc/bumblebee/bumblebee.conf file and Driver= make it Driver=nvidia 

```
gksudo gedit /etc/bumblebee/bumblebee.conf
``````
NoEcoModeOverride=false
# The Driver used by Bumblebee server. If this value is not set (or empty), 
# auto-detection is performed. The available drivers are nvidia and nouveau 
# (See also the driver-specific sections below) 
Driver=**nvidia**
```

save the file , logout - login or reboot and test again. (unity-support-test)

Thanks

---

### Post by pratikvasa on 2012-10-23
I did that..but the unity test still gives the same result..

```
/usr/lib/nux/unity_support_test -p
OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce GT 525M/PCIe/SSE2
OpenGL version string:  4.2.0 NVIDIA 295.40

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  no
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       no

```

---

### Post by NikTh on 2012-10-23
> **pratikvasa said:**
> 
hey i did not understand the link that you sent..can you please elaborate..thanks

Bug means error. Developers can fix an error (bug). The link-bug I gave (I think) is related to your problem. 
The only thing you can do , if a bug exists, is to wait until fixed. (Fix Released) or try to find a workaround (until bug fixed). We try this right now , but I am little dissatisfied with the progress. :(

We can try some things , but I am not sure if they work. I found this --> [http://askubuntu.com/questions/171470/how-to-make-unity-3d-work-with-bumblebee-using-the-intel-chipset](http://askubuntu.com/questions/171470/how-to-make-unity-3d-work-with-bumblebee-using-the-intel-chipset) , read the answer (green mark) to understand what is all about. 

Thanks

---

### Post by pratikvasa on 2012-10-24
Ok i will try doing what is specified in the link..

But if i am not successful is there a way in which I can always keep the nvidia active? I know its not energy efficient but still..

---

### Post by NikTh on 2012-10-24
Nvidia is active. You can see it from the results of unity-support-test. 

> ```
OpenGL vendor string:   NVIDIA Corporation 
OpenGL renderer string: GeForce GT 525M/PCIe/SSE2 
OpenGL version string:  4.2.0 NVIDIA 295.40
```The problem here and the error (bug) is that cannot support the unity 3d environment. The link I gave , is a similar problem with yours and the guy there explains what happened and he solved. 

The easy way might be to disable completely the integrated intel card from the BIOS (if you have such option).
Thanks

---

### Post by pratikvasa on 2012-10-24
Hey I was trying to do what was mentioned in the link..

there is said the following

"The Nvidia driver installer is likely to destroy your existing libglx.so (in /usr/lib/xorg/modules/extensions) and libGL.so (in /usr/lib). Back those up before installing the driver. If you already lost them, you could get them back by resintalling xserver-xorg-core and libgl1-mesa-glx, but when I tried that the first time, it left my laptop in a bad state (black screen after login, had to go into recovery), so I would recommend getting those manually via dpkg-deb."

how do i use dpkg-deb to get the file?

thanks.

---

### Post by NikTh on 2012-10-24
I think that the most easy thing is to uninstall the proprietary drivers and then install again the open libraries with this command 

```
sudo apt-get install --reinstall libgl1-mesa-glx xserver-xorg-video-all xserver-xorg-core
```And then backup the mentioned libraries in a file and restore when you need. 

With dpkg you can retrieve  the mentioned packages from here : [http://packages.ubuntu.com/](http://packages.ubuntu.com/) as .deb files and then with the command 
```
sudo dpkg-deb -X <packagename>.deb /destination/directory
``` you can extract all the contents of the .deb package and search and find the mentioned libraries.

---

### Post by pratikvasa on 2012-10-24
Hey I tried everything..but nothing worked..
Then I just upgraded ubuntu from 12.04 to 12.10..
And everything is working now..
Thanks a lot for your help..:)

---

