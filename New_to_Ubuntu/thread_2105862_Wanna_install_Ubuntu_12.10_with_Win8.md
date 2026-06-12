---
title: "Wanna install Ubuntu 12.10 with Win8"
date: 2013-01-17
forum: New to Ubuntu
---

### Post by kmelkon on 2013-01-17
Hey there,
So I've installed Win8 in a separate partition and i wanna install ubuntu 12.10 on a different partition .. can you tell what should i do? and what are the precautions that i should take cuz i dont wanna end up with a Grub that can't see my Win8 like the last time ..

Thanks all

---

### Post by tlhIngan on 2013-01-17
Can you post more info about what you did the last time and your specific hardware?
As far as I know, GRUB should be able to see everything.

---

### Post by oldfred on 2013-01-17
Did you install Windows in BIOS/MBR or UEFI/gpt mode? 

But either way grub should find Windows and let you boot it. There is a bug in UEFI installs and you need to use Boot-Repair to add the correct chain load entry from grub menu to Windows efi.

       
WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)

---

### Post by kmelkon on 2013-01-17
> **oldfred said:**
> Did you install Windows in BIOS/MBR or UEFI/gpt mode? 

But either way grub should find Windows and let you boot it. There is a bug in UEFI installs and you need to use Boot-Repair to add the correct chain load entry from grub menu to Windows efi.

       
WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)
It's in MBR/BIOS mode and i've just disabled the fast boot thing in win8 .. i'll get to installing now and let you know what happens ..
thanks

---

### Post by oldfred on 2013-01-17
You have to know as you have to install Ubuntu in the same mode or else you will not be able to dual boot without massive hassle in UEFI/BIOS menu.

How you boot install liveCD/DVD/Flash is how it will install.

Post this, if drive is gpt then you are in UEFI mode as Windows only boots from gpt with UEFI. If MBR(msdos) then you are in BIOS mode.
       sudo parted /dev/sda unit s print

---

### Post by kmelkon on 2013-01-17
> **oldfred said:**
> You have to know as you have to install Ubuntu in the same mode or else you will not be able to dual boot without massive hassle in UEFI/BIOS menu.

How you boot install liveCD/DVD/Flash is how it will install.

Post this, if drive is gpt then you are in UEFI mode as Windows only boots from gpt with UEFI. If MBR(msdos) then you are in BIOS mode.
       sudo parted /dev/sda unit s print

UGH i'm so confused now. I will install ubuntu from a live usb.. will there be any problem ? and how do I assure that my windows is in MBR mode and that ubuntu will install in the same mode ?

---

### Post by oldfred on 2013-01-17
Again, if you have the new UEFI there are two modes and both should be available for either Windows or Ubuntu. And how you boot install media is how it will install or UEFI mode or BIOS mode.

Fortunately Boot-Repair can convert from one to the other. BIOS mode used grub-pc and UEFI uses grub-efi and the install is otherwise the same.

---

