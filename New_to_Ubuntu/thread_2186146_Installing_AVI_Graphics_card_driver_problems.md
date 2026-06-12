---
title: "Installing AVI Graphics card driver problems"
date: 2013-11-06
forum: New to Ubuntu
---

### Post by jessica.c.johns on 2013-11-06
Hi..  I just installed Ubuntu yesterday and it hasn´t installed a driver for my ATI graphics card. I&#7743; completely new at this and I am having trouble working out which card I have let alone which driver to install. Any help would be greatly appreciated :) 
Ubuntu 12.04


If this is any help:

jessica@Jessica-Laptop:~$ lspci -nn | grep VGA
00:01.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Device [1002:9900]




```
jessica@Jessica-Laptop:~$ sudo lshw -C video
[sudo] password for jessica: 
  *-display               
       description: VGA compatible controller
       product: Advanced Micro Devices, Inc. [AMD/ATI]
       vendor: Hynix Semiconductor (Hyundai Electronics)
       physical id: 1
       bus info: pci@0000:00:01.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=fglrx_pci latency=0
       resources: irq:49 memory:c0000000-cfffffff ioport:f000(size=256) memory:feb00000-feb3ffff
```

---

### Post by mastablasta on 2013-11-06
you are right. system info doesn't say what chip it is installed. what is the laptop model and brand?

otherwise if any additional proprietary drivers are available system will offer to install them. if they are nto available then opensource drivers will be used. so if this is an older mashicne you are probably stuck with opensource drivers. they are hit or miss it seems. mine work well on two cards i tested them on. but i've read some word really bad and in some laptops they draw a lot of power/battery. to get newer opesource drivers you can install xorg edgers PPA or latest ubuntu version 13.10.

---

### Post by Werne on 2013-11-06
> **jessica.c.johns said:**
> *-display               
       description: VGA compatible controller
       product: Advanced Micro Devices, Inc. [AMD/ATI]
       vendor: Hynix Semiconductor (Hyundai Electronics)
       physical id: 1
       bus info: pci@0000:00:01.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       **configuration: driver=fglrx_pci latency=0**
       resources: irq:49 memory:c0000000-cfffffff ioport:f000(size=256) memory:feb00000-feb3ffff
That's not right, if the drivers were not installed, that line would go like this:
```
configuration: driver=radeon latency=0
```
 Try running the following commands one by one and post the output of each:
```
cat /etc/X11/xorg.conf

fglrxinfo

glxinfo|grep OpenGL

dpkg --get-selections|grep fglrx
```

It's possible that you have ATI drivers but they aren't initialized correctly (or at all). And when you're posting the output, use the code brackets, or mark the output and press the hash in the toolbar above, it makes it easier to read.

---

### Post by jessica.c.johns on 2013-11-08
Thanks guys for your responses!! My laptop was bought March this year so its pretty new. It came with Windows 8...its a Samsung NP355V5C A03CA
 I did the commands requested. I can upgrade to 13.10 if that helps? 

```
jessica@jessica-laptop:~$ cat /etc/X11/xorg.conf

Section "Screen"
    Identifier    "Default Screen"
    DefaultDepth    24
EndSection

Section "Module"
    Load    "glx"
EndSection
```

```
jessica@jessica-laptop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Advanced Micro Devices, Inc.
OpenGL renderer string: AMD Radeon HD 7660G
OpenGL version string: 4.2.12217 Compatibility Profile Context 13.101


```

```
jessica@jessica-laptop:~$ glxinfo|grep OpenGL
The program 'glxinfo' is currently not installed.  You can install it by typing:
sudo apt-get install mesa-utils


```

```
jessica@jessica-laptop:~$ dpkg --get-selections|grep fglrx
fglrx-amdcccle-updates                install
fglrx-experimental-13                deinstall
fglrx-updates                    install


```

---

### Post by mastablasta on 2013-11-08
looks like your graphics driver is installed. what seems to be the problem?

oh and as it says...: to get result from glxinfo|grep OpenGL


you need to first insztall glxinfo which you do by: 
sudo apt-get install mesa-utils

or finidng mesa utils package in software center and click install.

otherwise 13.10 should have better support for newer hardware. they do bring patches back to 12.04 but i am not sure if all of them go into 12.04. probably not.

---

### Post by Werne on 2013-11-08
Okay, you have fglrx-updates installed, which is the AMD graphics driver. You also have AMD Catalyst Control Center installed as well. No mesa-utils, bummer, I was sure Ubuntu came with mesa-utils. But that don't matter since fglrxinfo works, so we have the graphics chip model. :D
```
AMD Radeon HD 7660G
```
And we know you have a laptop/notebook with a Trinity quad-core A10-4600M mobile CPU, nice, that specific APU is pretty good and overclocks like crazy with a good mobo. Hope you have speedy RAM too in order to take full advantage of that thing.

The only problem I can see is that your xorg.conf is not like it should be, meaning fglrx hasn't been initialized after installation. Although fglrx should work regardless of that, run the following command to be sure, then reboot:
```
sudo aticonfig --initial
```
And you should have fully functioning AMD drivers after that. ;)

---

### Post by jessica.c.johns on 2013-11-08
Awesome, thanks so much for the help guys! All seems to be working perfectly now. :)

---

