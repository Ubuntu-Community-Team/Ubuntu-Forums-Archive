---
title: "updated to 8.04?? video card installed??"
date: 2008-07-01
forum: New to Ubuntu
---

### Post by broekskw on 2008-07-01
ok its been some time but everything was working great on 7.10 so updated to 8.04 and i think my video card driver is not working or installed (think in 7.10 was also not installed)what is the command to type in a terminal to find system spec to see if my card is there and the driver installed or not

thanks for all replies

---

### Post by phidia on 2008-07-01
[This]("https://help.ubuntu.com/community/Video") is a great guide for all things to do with getting your video card working.

> lspci | grep VGA will get you your card info. And looking at /etc/X11/xorg.conf in the device section will show you what driver is being used.

---

### Post by broekskw on 2008-07-01
Thanks phidia will look at this guide:popcorn:

---

### Post by broekskw on 2008-07-01
can any one help me on this 

Enable accelerated the accelerated ATI graphics driver in the restricted-manager, then do: 

how do i find "restricted-manager" in 8.04

looked in systems-preference ans also administration but with no luck

---

### Post by phidia on 2008-07-01
In heron it's no longer "restricted drivers" it's been renamed to "Hardware Drivers", and it is in System>Administration.

---

### Post by broekskw on 2008-07-01
great thanks again phidia

in my "Hardware Drivers" nothing is there, so do i need to follow that guide you posted:popcorn:

not having much luck with that guide???

---

### Post by broekskw on 2008-07-01
morning everyone, trying to get my ati rv2800 radeon 9200 se driver going with this guide
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

but on the first section under Instructions for Ubuntu 8.04 (Hardy)

Enable accelerated the accelerated ATI graphics driver in the restricted-manager, then do:

sudo dpkg-reconfigure -phigh linux-restricted-modules-`uname -r`
sudo insmod /lib/modules/`uname -r`/volatile/fglrx.ko

when i input that command in a terminal all i get back is 

broekskw@broekskw-desktop:~$ sudo insmod /lib/modules/`uname -r`/volatile/fglrx.ko
insmod: error inserting '/lib/modules/2.6.24-19-generic/volatile/fglrx.ko': -1 Operation not permitted

lost from here, any help:confused:
what im i doing wrong

thanks

broekskw@broekskw-desktop:~$

---

### Post by broekskw on 2008-07-01
this may be a stupid question but will this guide install the 

ATi 8.443.1-1 and above binary drivers

or do i have to find this driver first and install the do this guide??

thanks

---

### Post by phidia on 2008-07-01
Sometimes a distro upgrade will cause problems compared to a clean install.
Your drivers should have showed in the Hardware Drivers section.
Have you already tried [this howto]("http://ubuntuforums.org/showthread.php?t=515573")?

---

