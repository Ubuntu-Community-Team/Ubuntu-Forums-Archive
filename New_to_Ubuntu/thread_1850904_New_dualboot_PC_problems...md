---
title: "New dualboot PC problems.."
date: 2011-09-27
forum: New to Ubuntu
---

### Post by naragam on 2011-09-27
Hi all,

I just got my dual boot (Ubuntu 10.04 and Windows 7) PC ....but Ubuntu does NOT boot to Gnome desktop. It goes to power save mode immediately....HELP! 

Windows 7 boot works fine...

Nash

---

### Post by technosysind on 2011-09-27
Please confirm if it is able boot upto the login screen or not?

---

### Post by naragam on 2011-09-27
The initial grub menu for booting to Windows or Ubuntu comes up and for some odd reason if I select the very first (default) option it goes in to power save mode after displaying the initial Ubuntu screen. If I select a second option that says "Linux 2.6.32-33-generic (recovery mode)" it boots up the grub bios for me to login...but I have no idea of admin password or whatever su it assumes on recovery mode. This is supposedly a freshly loaded Ubuntu in a dual boot-up mode along with factory installed Dell Windows 7 professional.

Will that help to diagnose my problem? 

TiA, Nash

---

### Post by oldfred on 2011-09-27
The login for recovery is the same as you assigned when you installed. It is the same password you have to use anytime you use sudo.

[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

You may be having video issues. What video card do you have? 

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by naragam on 2011-09-27
Yeah, it could be a video problem.... I have a new 22" HD capable monitor and the DVI connector, but ubuntu might have been configured for the wrong card (VGA?). How do I check the hardware details in the grub mode or some other basic non-interactive and textual mode and fix the problems if there are some?

Also, can I boot Ubuntu to terminal mode and reset the graphics as required from a CDROM/DVD boot? I have a Ubuntu 10.04 disk...What docs can you point me to do this?

Thanks much,

Nash

---

### Post by oldfred on 2011-09-27
It is the Video card more than the monitor. Nomodeset works for nVidia and some others, generic often defaults to a minimum mode. Then you can often install the proprietary drivers if any.

Some other settings:
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)
* Older Intel video card: i915.modeset=1 or i915.modeset=0
* nVidia: nomodeset
* Generic: xforcevesa or nouveau.modeset=0
* Radeon: radeon.modeset=0

---

### Post by LinuxFan999 on 2011-09-27
@naragam
Which video card do you have?

---

### Post by naragam on 2011-09-27
Sorry, I don't know and am trying to figure out...the PC came pre-installed with both OS's from our IT dept.....:( I'll find out more tomorrow...hopefully! I chose not to pay our IT $1000 maintenance fee per year for Linux.....!

Nash

---

### Post by oldfred on 2011-09-27
This may help:

#To see video:
sudo lshw | grep -A 11 display

---

### Post by naragam on 2011-09-28
Yeah, it might help...but right now I'm not sure how I can get into the system w/o being able to login as anybody? Is there a way to get into mini-unix-like terminal at startup? Some kind of Fx key interrupt? I can't even boot from CD and even if it did boot, I see a dark screen.....

Nash

---

### Post by oldfred on 2011-09-28
From CD when you get the very first screen with a small person & keyboard, it means hit a key if you have issues. You then get a menu and with f6 can add nomodeset or other parameters.

---

