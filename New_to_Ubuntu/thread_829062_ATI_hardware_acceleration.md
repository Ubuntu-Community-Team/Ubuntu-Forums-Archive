---
title: "ATI hardware acceleration"
date: 2008-06-14
forum: New to Ubuntu
---

### Post by Dbugger on 2008-06-14
When I activate the ATI hardware acceleration, and I restart the computer, i get a black screen, instead of the login.

Im using Hardy. this is my lspci

> 00:00.0 Host bridge: ATI Technologies Inc Unknown device 5a31 (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 83)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (rev 80)
00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200M]
02:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:07.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)
02:09.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b4)
02:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 18)
02:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller
02:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 09)
02:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 04)

---

### Post by azimuth on 2008-06-14
I am not familiar with your particular ATI card, but on my Radion 9500 Pro the default open source drivers work fine for Compiz and the 3D games in the repositories. You may want to try them out before going to the restricted drivers.

---

### Post by Rocket2DMn on 2008-06-14
You can reconfigure X by rebooting into the recovery mode kernel (second option and grub) and running
```
dpkg-reconfigure xserver-xorg -phigh
reboot
```
Let the computer restart normally, then post for us your video card:
```
lscpi | grep VGA
```
Older ATI cards (9500 or so and older) don't use restricted/proprietary fglrx drivers.

---

### Post by Dbugger on 2008-06-15
I've been reading around and it seems like it's something to do with the MESA drivers, dont letting the ATI drivers to take control, but I still cant get it to run! :(

> ugger@dbugger-laptop:~$ lspci | grep  VGA
01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200M]

> dbugger@dbugger-laptop:~$ fglrxinfo 
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.3-rc2)

---

### Post by Rocket2DMn on 2008-06-15
I don't think that video card is compatible with the fgrlx restricted drivers, so you should uninstall them:
```
sudo apt-get remove --purge xorg-driver-fglrx
```
Then reconfigure X with
```
sudo dpkg-reconfigure xserver-xorg -phigh
```
Now restart X with CTRL+ALT+BACKSPACE
You can follow this guide to allow compiz to work - [http://ubuntuforums.org/showthread.php?t=764633](http://ubuntuforums.org/showthread.php?t=764633)

---

### Post by Dbugger on 2008-06-15
But it worked fine with gutsy....the problem started when i moved to hardy...

---

### Post by Rocket2DMn on 2008-06-15
I understand, but Hardy is using a new version of X which has some differences from the previous version - specifically, it relies more on autodetection than xorg.conf.  Did following the advice in my last post help?

---

### Post by Dbugger on 2008-06-15
> **Rocket2DMn said:**
> I understand, but Hardy is using a new version of X which has some differences from the previous version - specifically, it relies more on autodetection than xorg.conf.  Did following the advice in my last post help?

I did what you said, and... well, everything looks pretty much the same.

In "System -> Administration -> Hardware Drivers" the "ATI hardware accelerated" says "not enabled". And of course compiz doesnt work. It gives me a white screen of death for 30 seconds.

---

### Post by Rocket2DMn on 2008-06-15
Can you please post the output of
```
compiz --replace
```

---

### Post by Dbugger on 2008-06-15
> **Rocket2DMn said:**
> Can you please post the output of
```
compiz --replace
```

Here it is:

> dbugger@dbugger-laptop:~$ compiz --replace
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
Attempted to unregister path (path[0] = org path[1] = freedesktop) which isn't registered
Attempted to unregister path (path[0] = org path[1] = freedesktop) which isn't registered
Attempted to unregister path (path[0] = org path[1] = freedesktop) which isn't registered

this gave me a white screen so I had to leave with CTRL+C

---

### Post by Rocket2DMn on 2008-06-15
It sounds like your compiz is messed up, let's try to reinstall it.
```
sudo apt-get install --reinstall compiz
```
Otherwise you may get better support in the Desktop Effects and Customization forum - [http://ubuntuforums.org/forumdisplay.php?f=330](http://ubuntuforums.org/forumdisplay.php?f=330)
Remember, because the open source "ati" drivers are blacklisted for compiz, you may not get it to work at all, but it's worth posting in the other forum.

---

### Post by Dbugger on 2008-06-16
It didnt work. THank you for your help, I'll try in the other forum section.

---

