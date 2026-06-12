---
title: "Linux N0ob here. Installed Ubuntu alongside W10 from USB, it installs correctly, but"
date: 2016-09-09
forum: New to Ubuntu
---

### Post by jaythemann on 2016-09-09
[h=2]Linux N0ob here. Installed Ubuntu alongside W10 from USB, it installs correctly, but it just boots into Windows.[/h][COLOR=#333333][FONT=Ubuntu]I tried reinstalling from the USB, but no luck. When I reinstalled, it said Ubuntu was installed. I tried to figure out how to change my boot order, but I couldn't find anything.[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]Sorry for the noob post! I'm sick of windows, and help would be great.[/FONT][/COLOR]

---

### Post by RobGoss on 2016-09-09
Hello and welcome to the forum, I'm a bit confused because you mention you had to reinstall Ubuntu was there something wrong with your first installation?

Are you trying to dual boot Windows 10 and Ubuntu?

What steps have you taken to create the installation media and **USB** stick for your installation. Providing some information about your machine will also be helpful to others. Is this machine a new one and does if have** UEFI** ? I suggest reading this helpful tutorial it has some very good information that will come in handy [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

If your machine is in fact **UEFI **and Windows in installed in **UEFI mode, **then you need to install Ubuntu in the same way** UEFI**. 

If your machine has Windows installed in **Legacy  mode, **then you will need to install Ubuntu in** Legacy mode**.

A word to the wise, if you're new to Linux and Ubuntu, you will certainly have to do your home work before you attempt to dual boot your machine because if done incorrectly, you can wipe out your entire system and that's no fun.

---

### Post by yancek on 2016-09-09
Details on dual booting Ubuntu with windows 10 are at the Ubuntu documentation site below.  Compare that to what you did.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by Geoffrey_Arndt on 2016-09-10
Dual-boot installs on PC's since about 2010-2011 has been a "ROYAL PITA" in many cases.    It used to be "relatively" easy to set up dual-boots.   Not any more.

Many PC types/brands are stealthily designed to run Windows only - - unless one goes to extraordinary lengths to modify boot loader files, turn off default Windows settings such as quick/fast boot, secure boot, setting up HDD unallocated space, etc.   The list is often long.

So, these days, I just opt to get my Linux installed the same way I did Windows prior to 2003 - - buying PC's with Linux pre-installed.    Set up time and simplicity is about the same as a typical tablet or smart phone (10 minutes?).   Plus, if absolutely needing a dual-boot, several vendors now offer that service on new Linux PC's for a small fee (about $35 to $75 on average).   See the link in my signature for more detail.

NOTE:  if needing to buy a Windows PC that you think, at a later time, you may need to install Linux on . . do your homework first.   Opt for such brands as Lenovo Thinkpads (very Linux friendly) or many Dell systems.   Look for "All-Intel " - meaning Intel graphics and Intel Networking/Wireless.   Plus Lenovo and Dell do a better job complying with the UEFI spec.   Avoid Asus, Acer, HP, Toshiba, Samsung.

---

