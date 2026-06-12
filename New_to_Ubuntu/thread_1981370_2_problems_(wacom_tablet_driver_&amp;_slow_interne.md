---
title: "2 problems (wacom tablet driver &amp; slow internet)"
date: 2012-05-16
forum: New to Ubuntu
---

### Post by art student owl on 2012-05-16
hi people

I installed Ubuntu 12.04 lts on my laptop the other day.
My laptop normally runs windows 7, but since I installed ubuntu, you have the option to choose between windows and ubuntu during startup. 

I'm completely new to ubuntu and ran into some problems. 

The first one is that I cant get my 'wacom bamboo pen' to work with ubuntu. I searched the web and also this forum but I couldn't find the solution for me. when I click 'system settings' in the launcher it shows an icon 'wacom graphics tablet', but when you click that one it says no tablet was detected. what to do??

second problem is that since using ubuntu my internet connection seems to work a lot slower. youtube video's for example load the first minute really quick, but from there it takes ages. 
Is that an effect of using ubuntu instead of windows? 

cheers,
art student owl

---

### Post by Favux on 2012-05-16
Hi art student owl,

Welcome to Ubuntu forums!

Not sure how much help I can be on the internet problem.  Hopefully someone else will chime in.  Since the download speed seems fine at first it does sound like some setting/configuration may not be right.  A buffer filling too quickly, like a too small tmp file?

For the Wacom Bamboo Pen what model is it?  It should be on the bottom of the tablet.  Also open a terminal and run this command:
```
lsusb
```
and post the output.  That should give us the PID (product ID) of the tablet.  And that will tell us if we need to do anything.

---

### Post by art student owl on 2012-05-17
hi, thanks for helping me!

the model of my tablet is CTL-240/k. 
the command
```
lsusb
```
gives this as output:

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 064e:d20c Suyin Corp.

---

### Post by art student owl on 2012-05-17
o, sorry, and with the device plugged in the output for
```
lsusb
```
gives:


Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 064e:d20c Suyin Corp. 
Bus 006 Device 003: ID 056a:00dd Wacom Co., Ltd 

art student owl

---

### Post by idoitprone on 2012-05-17
does this thread help?
[https://bbs.archlinux.org/viewtopic.php?id=131831](https://bbs.archlinux.org/viewtopic.php?id=131831)

---

### Post by art student owl on 2012-05-17
I really don't know how all this stuff works. 
I downloaded the files I was supposed to and typed the codes in the terminal, but I get reactions like: 'no such file or directory' an 'acces denied'. 

I allready tried a few of those things I found on the web, and some seem to install properly, but none of them make the tablet work. 

is there no simple way to do this, without codes and stuff? ubuntu seems to be a graphic interface after all??

---

### Post by art student owl on 2012-05-17
wich doesn't mean I don't want to learn, but I cant figure it out by myself yet.

---

### Post by Favux on 2012-05-17
Hi art student owl,

You have a third generation BambooPT, released 10/11.  So support for it didn't get added until the 3.3 kernel.  Unfortunately Precise 12.04 has the 3.2 kernel.  This means the usb Wacom kernel driver called wacom.ko, doesn't have your model the CTL-270/K; Product ID = 0xdd in it.

This all described at the top of the [BambooPT HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562").  To get a wacom.ko you need to compile one from input-wacom.  Input-wacom is a package provided by the Linux Wacom Project to backport kernel support for new model tablets to older kernels.  That's part I. on the HOW TO.  It looks intimidating but it isn't hard.  Just follow the step by step instructions and Copy and Paste.  Skim through it a couple of times to get a "feel" for what you are going to do.  After you've done it once or twice it just takes a few minutes to do again.  Half the time is waiting for it to reboot.

Or your other option is install a PPA with at least input-wacom 12.0.  And just before part I. on the HOW TO is a link to Lekensteyn's PPA which has input-wacom-0.12.1.

Remember Lekensteyn's PPA adds the wacom.ko kernel module through dkms, which is dynamic kernel module support.  What that means is when Ubuntu updates your kernel through Updates the wacom.ko module will automatically get updated to include your model.  Otherwise you'll need to recompile the wacom.ko from input-wacom each time a kernel update comes along.  Which isn't that often.

Why then not always use a PPA with dkms?  Because if you forget it is installed and forget to uninstall it when you want to compile a new wacom.ko, say for a new tablet, the dkms wacom.ko will block it from working.  You have to remember to uninstall the PPA first.

---

### Post by art student owl on 2012-05-18
Thanks for the help Favux! I hope I can make it work now!

---

### Post by art student owl on 2012-05-18
okay great just got the stuff working! thanks!

---

### Post by Favux on 2012-05-18
Great!  Nice job.  :)

---

