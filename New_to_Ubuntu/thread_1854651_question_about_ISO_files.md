---
title: "question about ISO files"
date: 2011-10-04
forum: New to Ubuntu
---

### Post by VtecHonda on 2011-10-04
hey all. 

is it possible to boot from an iso file? 

i just finished a custom built pc, and i have my OS (win7) as an ISO on a CD, but when i try to boot from the CD, it just wont boot. (i burned it on the cd using cdburnerxp, i know.......u might say: why are u still using windows? but this is a different machine than my linux one). 

am i missing something? any help would be greatly appreciated.

or are there any alternatives to using a cd?

will booting from a usb work? can someone explain this process? (because i currently do not have a flash drive with free space on it). 

thanks everyone.

---

### Post by brpylko on 2011-10-04
did you use the burn iso option or just burn it like a regular file?

you need to use the burn iso option or it will not work

if it still does not work try using a tool specifically for creating windows disks such as RT SE7en lite(OK that might be a little over the top ;)).

It is possible to boot from a USB storage device. I do not know how to do this but I am sure you con find a tutorial online.

---

### Post by drs305 on 2011-10-04
It is possible to boot from an Ubuntu ISO file, and many of the other Linux variants. Grub 2 allows the user to boot these ISO files if they were constructed to do this (the last 3 or 4 Ubuntu releases can do it). 

Unfortunately, I don't know if Windows can do it. I've not seen that capability via Grub at least.

For booting Ubuntu ISOs, if you are interested, click the following link:[ISO Booting with Grub 2]("ubuntuforums.org/showthread.php?t=1549847")

You can also install Ubuntu from an Ubuntu ISO. There is a section in this thread describing it:
[HOWTO: Boot & Install Ubuntu from the Grub Rescue Prompt]("http://ubuntuforums.org/showthread.php?t=1599293")

As far as your current situation, have you checked the ISO file for integrity and also tried a commerical CD in the drive to ensure it is working?

---

### Post by Mark Phelps on 2011-10-05
You could also try burning the ISO image in Windows using ImgBurn.  It's a free download and one of the best image burners out there for Windows.

---

### Post by collisionystm on 2011-10-05
If you are using windows

Use this to burn your .iso to a disc.

[http://isorecorder.alexfeinman.com/isorecorder.htm](http://isorecorder.alexfeinman.com/isorecorder.htm)

Windows 7 will only fit on a dvd. If you somehow got a version that fits on a CD you def are not using Win 7. "Get" another copy.

---

### Post by Frogs Hair on 2011-10-05
I always make my Ubuntu discs from Windows 7 with no additional software . I just have to select the option to make it bootable when the dialog opens.

You can also use a USB . [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by meatytaco on 2011-10-05
Another alternative for booting from USB would be to use the Linux Live USB Creator. It's easy to use, and you can use it as linux live with persistence or install from it. :)

[http://www.linuxliveusb.com/]("http://www.linuxliveusb.com/")

Edit: Sorry, forgot you were wanting Windows, not Linux :S :S my bad.

---

### Post by binary00mind on 2011-10-05
> **collisionystm said:**
> If you are using windows

Use this to burn your .iso to a disc.

[http://isorecorder.alexfeinman.com/isorecorder.htm](http://isorecorder.alexfeinman.com/isorecorder.htm)

Windows 7 will only fit on a dvd. If you somehow got a version that fits on a CD you def are not using Win 7. "Get" another copy. Very good point about the DVD. 
Besides the one you mentioned I love the simplicity and reliability of Infrarecorder 
link for x64 bit 
[http://sourceforge.net/projects/infrarecorder/files/InfraRecorder/0.52/ir052_x64.msi/download](http://sourceforge.net/projects/infrarecorder/files/InfraRecorder/0.52/ir052_x64.msi/download) 
and x32 bit link:
[http://sourceforge.net/projects/infrarecorder/files/InfraRecorder/0.52/ir052.exe/download](http://sourceforge.net/projects/infrarecorder/files/InfraRecorder/0.52/ir052.exe/download) 

Plus you could use hash utility, I know excellent one also from SourceForge.net but forgot the name...use search while there. 

There is Hash Tab and Hash Calc-ulator for Windows to check hash but they are x32 bit and are chocking on larger files plus Hash tab not always shows in context menu (it is not x32 vs x64 issue) 

Here is the link to check Win 7 RC DVD, have no clue if it works on newer versions or it was only written for RC...only used once myself...link:
[http://www.istartedsomething.com/20090706/windows-7-iso-verifier/](http://www.istartedsomething.com/20090706/windows-7-iso-verifier/)

And last but not least do the burning on the slowest possible speed...using DAO (disk at once) or SAO (Session at once)

---

