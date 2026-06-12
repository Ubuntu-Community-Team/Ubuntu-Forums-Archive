---
title: "Ubuntu 13.10 won't install, after boot selection goes to a DOS looking prompt shell"
date: 2013-12-09
forum: New to Ubuntu
---

### Post by bellcurve0 on 2013-12-09
Hello all, I've been a windows user all my life and want to try Ubuntu and the world of Linux. I've setup a new machine (specs below if that helps) and am attempting to install/run Unbuntu 13.10 on said machine. So far the only thing I've managed to do is seemginly create alot of drink coasters lol

Stupid side question for experienced user of Linux, (I'd like to know what I'm getting into to set myself with the proper expectations) should I be expecting ubuntu to be as easy (to run, get drivers, software etc) and dependable as windows in general or not? 

Computer specs:

FX6300 CPU
Gigabyte 990fx-ud5 motherboard
8gb ram
5 x HIS R9 280x GPUs
- Samsung EVO SSD 120gb or kingston 16gb usb (blank to install OS on) = tried both options. Would like to learn how to run the OS on a usb stick if possible.

Goal: Once I get things working on this machine I would create multiple nodes with similar build specs to be able to run VCL to enable large scale parrallel processing.

Insofar as installation itself and whats happening:

*This is for a brand new system.

I've burned the ISO using the app "freeisoburner" (creation works, disk itself is fine) and alternatively creating a bootable usb using the program suggested by the Ubuntu download page. 

Via DVD player or usb stick (attempted multiple times, downloaded ISO multiple times etc) = Computer starts, gigabyte MB bios load sccreen displays, then switches to a basic DOS-like boot selection screen. Four options are given (try, install, OEM install, check for errors) - all options selected lead to a ubuntu load screen to which after a dozen seconds or so goes black and then simply displays a command prompt. I don't see any of the screens that the Ubuntu download page shows, I don't see any errors. I'm assuming there should be a log somewhere to see what errors are being creted.. but I'm new at this and so pretty ignorant as far as where said logs would be or how to access them. 

 So I'm starting to think (well reasonably sure) that I'm dealing with a hardware configuration issue (I hope that all it is). Any help would be greatly appreciated. Thx all.

---

### Post by codenine75a on 2013-12-09
I would check your boot options in BIOS and make sure it is set to boot to USB *first* or compact disk drive *first*  I can only guess that it is booting to a partition of the hard disk drive.

---

### Post by fantab on 2013-12-09
> **bellcurve0 said:**
> Hello all, I've been a windows user all my life and want to try Ubuntu and the world of Linux. .......
Stupid side question for experienced user of Linux, (I'd like to know what I'm getting into to set myself with the proper expectations) should I be expecting ubuntu to be as easy (to run, get drivers, software etc) and dependable as windows in general or not? 
.............
.............

Via DVD player or usb stick (attempted multiple times, downloaded ISO multiple times etc) = Computer starts, gigabyte MB bios load sccreen displays, then switches to a basic DOS-like boot selection screen. Four options are given (try, install, OEM install, check for errors) - all options selected lead to a ubuntu load screen to which after a dozen seconds or so goes black and then simply displays a command prompt. I don't see any of the screens that the Ubuntu download page shows, I don't see any errors. I'm assuming there should be a log somewhere to see what errors are being creted.. but I'm new at this and so pretty ignorant as far as where said logs would be or how to access them. 

 

First things first: [Linux is NOT Windows]("http://linux.oneandoneis2.org/LNW.htm")

The kind of problem you describe smells of either a bad 'burn' or Graphics card related.

Here's what you can try:
1. Do a [MD5Sum Check]("https://help.ubuntu.com/community/HowToMD5SUM") on the ubuntu.iso you've downloaded, to confirm the integrity of the download.
2. Lets use usb-stick.. Download [Unetbootin]("http://unetbootin.sourceforge.net/") and use it to Burn the ubuntu .iso.
__Boot with the usb-stick and "Try ubuntu without installing"... 

Do you have Windows on your "brand new system"? If 'yes', What version of Windows?
What Ubuntu version are you trying?


3. Try the '[nomodeset]("http://ubuntuforums.org/showthread.php?t=1613132&p=10069997#post10069997")' option to temporarily fix graphics issue.
This option lets you to run the 'installer' in a 'failsafe graphics' mode. 

I'd say try the third option first...

---

### Post by newb85 on 2013-12-09
+1 to using the nomodeset option.   It sounds to me like your graphics card won't run on the generic drivers.  What kind of graphics card is it?

---

### Post by bellcurve0 on 2013-12-09
> **codenine75a said:**
> I would check your boot options in BIOS and make sure it is set to boot to USB *first* or compact disk drive *first*  I can only guess that it is booting to a partition of the hard disk drive.

Thx for the reply. Yes I've moved the boot options around when I tried with the compact disk drive and alternatively with the usb stick, made sure to have them first. Disabled booting from ssd (for a few attempts to make sure, didn't change anything).

---

### Post by bellcurve0 on 2013-12-09
> **fantab said:**
> First things first: [Linux is NOT Windows]("http://linux.oneandoneis2.org/LNW.htm")

The kind of problem you describe smells of either a bad 'burn' or Graphics card related.

Here's what you can try:
1. Do a [MD5Sum Check]("https://help.ubuntu.com/community/HowToMD5SUM") on the ubuntu.iso you've downloaded, to confirm the integrity of the download.
2. Lets use usb-stick.. Download [Unetbootin]("http://unetbootin.sourceforge.net/") and use it to Burn the ubuntu .iso.
__Boot with the usb-stick and "Try ubuntu without installing"... 

Do you have Windows on your "brand new system"? If 'yes', What version of Windows?
What Ubuntu version are you trying?


3. Try the '[nomodeset]("http://ubuntuforums.org/showthread.php?t=1613132&p=10069997#post10069997")' option to temporarily fix graphics issue.
This option lets you to run the 'installer' in a 'failsafe graphics' mode. 

I'd say try the third option first...

Brand new setup, no previous OS. Trying to load up and install Ubuntu 13.10.
GPU is the HIS R9 280X IceQ2 Turbo Boost

Thx for advice, I'll give it a whirl.

---

### Post by bellcurve0 on 2013-12-09
> **newb85 said:**
> +1 to using the nomodeset option.   It sounds to me like your graphics card won't run on the generic drivers.  What kind of graphics card is it?

The GPU is just a radeon card. HIS R9 280x iceQ2 turbo boost.

---

### Post by newb85 on 2013-12-09
I've installed Ubuntu for a friend on a machine with an ATI Radeon graphics card, and in that case, nomodeset was necessary.

Edit: that's not to say it's always necessary for Radeon.  I don't know that.  But hey, it's worth a try.

---

### Post by bellcurve0 on 2013-12-09
> **fantab said:**
> First things first: [Linux is NOT Windows]("http://linux.oneandoneis2.org/LNW.htm")

The kind of problem you describe smells of either a bad 'burn' or Graphics card related.

Here's what you can try:
1. Do a [MD5Sum Check]("https://help.ubuntu.com/community/HowToMD5SUM") on the ubuntu.iso you've downloaded, to confirm the integrity of the download.
2. Lets use usb-stick.. Download [Unetbootin]("http://unetbootin.sourceforge.net/") and use it to Burn the ubuntu .iso.
__Boot with the usb-stick and "Try ubuntu without installing"... 

Do you have Windows on your "brand new system"? If 'yes', What version of Windows?
What Ubuntu version are you trying?


3. Try the '[nomodeset]("http://ubuntuforums.org/showthread.php?t=1613132&p=10069997#post10069997")' option to temporarily fix graphics issue.
This option lets you to run the 'installer' in a 'failsafe graphics' mode. 

I'd say try the third option first...

Also, thank you for the great link above (Linx is not windows). Was a great read and demonstarted how uninformed I was about Linux in general.

---

