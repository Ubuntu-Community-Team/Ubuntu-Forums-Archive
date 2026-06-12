---
title: "Ubuntu 12-10 Virtualbox no fullscreen after guest additions install"
date: 2012-10-27
forum: New to Ubuntu
---

### Post by Dean_Grobler on 2012-10-27
Hi there,

I have Ubuntu 12-10 64bit running in a virtualbox ontop of Windows 7 Professional 64bit.

I'm just trying to get my virtual machine to display fullscreen, and after installing the guest additions and rebooting the virtual machine, it's still not displaying in fullscreen mode.

Any ideas anyone?

---

### Post by wyd on 2012-11-12
I've the same problem.. Any solution ?

---

### Post by newb85 on 2012-11-12
What version of Virtualbox are you running?

---

### Post by NikTh on 2012-11-13
Try to install the guest additions included in the guest OS  ,  and **not from the Oracle's Virtual CD/DVD**. 

In other words. If now you have installed guest additions from Virtual CD/DVD , boot to the Virtual OS (guest) and open a terminal and do 

```
cd /opt 
sudo ./blahblahblah.run
```<blahblahblah.run> is the script for uninstall the guest additions. I don't remember the name , use [TAB] to auto-fill. 

After that , reboot your Virtual OS. 
Then open a terminal again and do 
```
sudo apt-get install virtualbox-guest-x11 virtualbox-guest-dkms virtualbox-guest-utils
```after the installation finish , reboot. 
Is it OK now ? 

Thanks

---

### Post by gwi on 2012-11-14
I am having the same problem, with the opposite setup: host is Linux, guest is Windows XP.

If I try to maximize the window, part of the border dissapears (see first two screenshot fragments), and the window does not fill the entire display. Even part of the icons in the Virtualbox statusbar is missing.

If I switch fo fullscreen mode, the border and Virtualbox menu and statusbar disappear, but the part of the display showing the guest desktop, does not change size or position. The borders are just replaced by a black area (as shown in the last two screenshot fragments).

It all used to work perfectly. I have no idea what is wrong now.

Edit:
I have another vm running Windows XP. This one has Guest Additions version 4.0.4 installed, and this one correctly displays maximised. So my guess would be there is something wrong with the newer guest additions.

---

### Post by tplevrak on 2013-03-22
@ NickTh

Worked like a charm

Thanks a lot !!!!

---

