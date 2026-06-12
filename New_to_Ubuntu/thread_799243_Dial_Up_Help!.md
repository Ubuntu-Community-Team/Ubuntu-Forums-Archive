---
title: "Dial Up Help!"
date: 2008-05-18
forum: New to Ubuntu
---

### Post by rocketman_dc on 2008-05-18
I've almost gotten xubuntu where I need it, but I'm flailing on dialup and modem installation.  I have an internal modem that the manufacturer swears runs in Linux, and I think it's my complete lack of understanding of how to work in Linux that is the problem.  I don't know how to run basic tar things so I haven't been able to run that scan modem program.  First, can someone walk me thru the absolute basic of downloading a program like that and using it.

More specifically, my modem came with a help sheet for Linux.  It says:

"various versions of Linux drivers included (on cd) 
For the latest version for 2801 modem go to
cdrom:\pci modem card\smlink\2801\linux
copy to your linux system
become root
su -
rpm -ivh hsfmodem-7.60.00.00oem-1.i386.rpm

to uninstall from your system
rpm -e $(rpm -qa | grep hsf)

if your kernal is compiled with config...4kstacks then most likely you'll need to recompile without the cpnfig...4kstacks option

for old kernals and modem drivers visit camnix.com/drivers
www.camnix.com"

I think I installed the rpm thing somehow, but when I use su - it asks for a password, and the login password doesn't work.  I was able to get to the directory on the cdrom through the file manager, but I didn't know what to do when I got there (and clicking around didn't seem to yield any results.)  I was not able to get to the directory in the terminal.  I'm totally lost.  I'm going to give up if I can't get this modem and dial up to work.

I did find the Network thing and I put in a phone number and password for dial up, and I chose dial up as first choice for internet, but no dialing up ever happened.

thanks very much.

---

### Post by spiderbatdad on 2008-05-18
This site can be very helpful:[http://132.68.73.235/linmodems/index.html](http://132.68.73.235/linmodems/index.html)

Provides a link to get the scanmodem tool and instructions for using it. Scroll down to # .8

---

### Post by HotShotDJ on 2008-05-18
> **rocketman_dc said:**
> I have an internal modem that the manufacturer swears runs in LinuxWho is the manufacturer.  If you are using a Dell (please provide model) then it should be very simple... no tarballs or rpm files.

---

### Post by rocketman_dc on 2008-05-19
The manufacturer is not identified.  The site is [http://www.camnix.com/](http://www.camnix.com/)

---

