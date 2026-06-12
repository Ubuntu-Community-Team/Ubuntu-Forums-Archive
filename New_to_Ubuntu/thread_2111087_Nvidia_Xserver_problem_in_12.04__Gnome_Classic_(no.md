---
title: "Nvidia Xserver problem in 12.04 / Gnome Classic (no effects)"
date: 2013-02-01
forum: New to Ubuntu
---

### Post by Stunt Double on 2013-02-01
On 2 different computers, a Dell GX270 and a Gateway GM5424, when I attempt to check my resolution via Applications-->Administratiom-->Nvidia XServer Settings-->X Server Display Configuration---I get this message: Unable to load X Server Display Configuration page: the NVIDIA X driver on (GX270 or GM5424) is not new enough to support the nvidia-settings Display Configuration page.
   I have the additional drivers installed.
   It's puzzling because when I first set-up the computers, I was able to set the monitor resolution without getting that message. And the resolution has remained correct, but I can't change it now.
Thanks

---

### Post by omeomi on 2013-02-01
Does it still give the same error if you run Nvidia settings as root?

```
gksudo nvidia-settings
```

---

### Post by NikTh on 2013-02-01
Hi  
also some info would be useful for us to understand the nature of the problem. 

Open a terminal (CTRL+ALT+T) and post back the results of below commands

```
lsb_release -rcd ; uname -r 
dpkg -l | grep -i nvidia
lspci -nnk | grep -iA2 vga
``` 

_Please click on **"New Reply"** and put the results inside [CODE] tags to be easier to read._ [See here how]("http://i.stack.imgur.com/zADbK.png")

Thanks

---

### Post by Stunt Double on 2013-02-01
Same result with gksudo nvidia-settings.

Results from the other three:

```
dinolathe@dinolathe2:~$ lsb_release -rcd ; uname -r 
Description:	Ubuntu 12.04.1 LTS
Release:	12.04
Codename:	precise
3.2.0-37-generic-pae
dinolathe@dinolathe2:~$ dpkg -l | grep -i nvidia
ii  nvidia-173                                    173.14.35-0ubuntu0.2                    NVIDIA binary Xorg driver, kernel module and VDPAU library
ii  nvidia-common                                 1:0.2.44.2                              Find obsolete NVIDIA drivers
ii  nvidia-current                                295.40-0ubuntu1.2                       NVIDIA binary Xorg driver, kernel module and VDPAU library
ii  nvidia-current-updates                        304.64-0ubuntu0.1                       NVIDIA binary Xorg driver, kernel module and VDPAU library
ii  nvidia-experimental-310                       310.14-0ubuntu0.2                       Experimental NVIDIA binary Xorg driver, kernel module and VDPAU library
ii  nvidia-settings                               295.33-0ubuntu1                         Tool of configuring the NVIDIA graphics driver
ii  nvidia-settings-updates                       304.43-0ubuntu0.2                       Tool of configuring the NVIDIA graphics driver
dinolathe@dinolathe2:~$ lspci -nnk | grep -iA2 vga
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation Device [10de:0fc1] (rev a1)
	Subsystem: eVga.com. Corp. Device [3842:3645]
	Kernel driver in use: nvidia
	Kernel modules: nvidia_current, nvidia_173, nvidia_experimental_310, nvidia_current_updates, nouveau, nvidiafb
--
	Subsystem: eVga.com. Corp. Device [3842:3645]
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd-hda-intel
```

Thanks for the help.

---

### Post by NikTh on 2013-02-03
Hi , 
it seems that you have installed ALL the nvidia-drivers that are available.. and this is wrong. 

You can have ONE driver , not all together.

You graphics card is Nvidia GeForce GT640 , so I suggest you use the experimental-310 driver and see how is going.. 

Now lets clear up your system. 

Execute the commands below one by one.. 

```
sudo apt-get purge nvidia* 
sudo rm /etc/X11/xorg.conf 
sudo apt-get --purge autoremove 
sudo apt-get purge $(dpkg -l | awk '/^rc/ { print $2 }')
```Then install the experimental-310 ONLY.. 

```
sudo apt-get install nvidia-experimental-310 nvidia-settings-experimental-310
sudo nvidia-xconfig
```Then reboot your system and see if problem solved.. 

I want to see again the results of commands below
```
/usr/lib/nux/unity_support_test -p 
lspci -nnk | grep -iA2 vga
dpkg -l | grep -i nvidia
```Thanks

---

### Post by Stunt Double on 2013-02-05
I didn't install the latest experimental driver because I had tried it before with a poor result.
   Nvidia_current-updates worked perfectly. 

Here are the results:```

```dinolathe@dinolathe2:~$ /usr/lib/nux/unity_support_test -p
OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce GT 640/PCIe/SSE2
OpenGL version string:  4.2.0 NVIDIA 304.64

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes
dinolathe@dinolathe2:~$ lspci -nnk | grep -iA2 vga
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation Device [10de:0fc1] (rev a1)
	Subsystem: eVga.com. Corp. Device [3842:3645]
	Kernel driver in use: nvidia
	Kernel modules: nvidia_current_updates, nouveau, nvidiafb
--
	Subsystem: eVga.com. Corp. Device [3842:3645]
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd-hda-intel
dinolathe@dinolathe2:~$ dpkg -l | grep -i nvidia
ii  nvidia-current-updates                        304.64-0ubuntu0.1                       NVIDIA binary Xorg driver, kernel module and VDPAU library
ii  nvidia-settings-updates                       304.43-0ubuntu0.2                       Tool of configuring the NVIDIA graphics driver
```

``` 

Thanks for the help.

---

### Post by NikTh on 2013-02-09
Ok , very good. Use any driver that serves your needs and works flawlessly. 

Nvidia-current-updates (304.64) works good ? Then.. nvidia-current-updates indeed ! 

Please mark the thread as solved.. see my signature for a How To. 

Thanks

---

