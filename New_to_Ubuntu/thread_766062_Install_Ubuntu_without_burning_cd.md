---
title: "Install Ubuntu without burning cd"
date: 2008-04-25
forum: New to Ubuntu
---

### Post by noorez on 2008-04-25
Hi, I was trying to run the live version of 8.04 without burning the cd. I followed the instructions on this page: [http://ubuntuforums.org/newthread.php?do=newthread&f=326](http://ubuntuforums.org/newthread.php?do=newthread&f=326) but it did not work. The boot process stoped at a prompt with something like: (initrdfs) ?

I took a look at the casper.log at this prompt and it showed an error that it couldn't find a device /dev/scd0 ??... I then tried to run of the 'live partition again but this time I put in a cd with 8.04 on it and it booted, from the cd??'. Does anyone know how to fix this?

---

### Post by seshomaru samma on 2008-04-25
The link you posted is wrong
Were you trying to use Wubi or something?

If you got an OS on your computer (Windows or Linux) you can install Ubuntu with [Unetbootin]("http://unetbootin.sourceforge.net/")

---

### Post by noorez on 2008-04-25
Sorry....here is the link:

[https://help.ubuntu.com/community/Installation/FromLinux](https://help.ubuntu.com/community/Installation/FromLinux)

---

### Post by seshomaru samma on 2008-04-25
If you have an already burnt CD -use that to install Ubuntu the usual way

The link you followed is for those who do not have a CD-rom , it's a little bit unusual
If you don't have a CD -use Ubootnetin - I gave you the link in my previous post

---

### Post by kpkeerthi on 2008-04-25
I installed hardy from a USB flash drive. 

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

* You need a working linux and a BIOS that could boot from USB drives.

---

### Post by marine63 on 2008-04-25
download virtualbox and install it and virtual machine it
To install ubuntu physically get your hands on vmware workstation (i think vmware server will do...) and when making a new virtual machine do new virtual machine >> custom >> and install physically instead of on a virtual harddrive ( requires you to fix the grub) (haven't done with 2 partition, easy with 2 physical harddrives)
change bios to run in harddrive with ubuntu is installed on
(i think if u have a windows xp cd you can run recovery mode and type in bootcfg if 2 partition but dont take my word for it...)
[http://ubuntuforums.org/showthread.php?t=739256](http://ubuntuforums.org/showthread.php?t=739256) (original thread)
fix menu.lst (grub)
> gksudo gedit /boot/grub.menu.lst  (in terminal) ( i think this is the command... if its not right look in the thread link i gave u)
original:
> ## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

rewrite as:
> ## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
# hiddenmenu
original:
> title Ubuntu 7.10, kernel 2.6.22-14-generic
root (hd0,0)
kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=413d63db-6a13-4427-9788-09be60eee48f ro quiet splash
initrd /boot/initrd.img-2.6.22-14-generic
quiet

title Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root (hd0,0)
kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=413d63db-6a13-4427-9788-09be60eee48f ro single
initrd /boot/initrd.img-2.6.22-14-generic

title Ubuntu 7.10, memtest86+
root (hd0,0)
kernel /boot/memtest86+.bin
quiet

add this:
> title Windows NT/2000/XP
root (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
savedefault
chainloader +1

---

