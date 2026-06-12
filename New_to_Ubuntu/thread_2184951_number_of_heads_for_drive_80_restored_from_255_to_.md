---
title: "number of heads for drive 80 restored from 255 to 16"
date: 2013-10-31
forum: New to Ubuntu
---

### Post by eagles.gift on 2013-10-31
Hi,

I just installed Ubuntu Studio 12.04 (64-bit) on a PC alongside Windows 8.1. and after I choose Ubuntu from the boot menu I see the following output:

> Initialize variable space...
Starting cmain ()...
!!number of heads for drive 80 restored from 255 to 16


Then underneath is a blinking cursor. I cannot type anything in and nothing happens after this point. I have searched online for a couple of hours and not found an answer so I thought I'd try my luck in here. I previously installed the same version of Ubuntu on this machine with no problems but that was when I was using Windows 7. I have an oldish, cheap mobo so UEFI is not an issue. I put grub on the root partition first of all and then when I had this problem I started the installation from scratch again and put it on the mbr of the main Windows partition to see if that would help, but it didn't. Any help would be very much appreciated.

Cheers

---

### Post by Mark Phelps on 2013-10-31
Unfortunately, that message is nonesense because, with two heads per platter, no consumer brand hard disk today is going to have eight platters!

What is means is that the BIOS setting for your hard disk geometry is all wrong.

Modern BIOSs generally come with an "auto" setting in which the BIOS queries the drive controller and determines the proper settings -- unless you have manually changed the BIOS setting yourself.

My suggestion is to boot into the BIOS settings and see if you can set them to "auto" for this drive.

---

### Post by eagles.gift on 2013-10-31
Thanks for your reply. I haven't changed any settings for hard disk discovery in the BIOS but I will check and make sure. I guess as I haven't yet done anything with the new installation (because I can't get in!) I could reinstall on another partition / drive and see if that helps (if the auto setting is already on).

I wasn't expecting any problems like this as I have installed 4 or 5 different Linux distros on my machine in the past (all at the same time) as well as PC-BSD, and never had any similar issues.

Thanks again for your suggestion. Will try it as soon as I am in front of my PC.

---

### Post by eagles.gift on 2013-11-01
Just to say I installed it on another partition / drive and no problems booting up now. I think grub had not installed properly when I did it previously. I didn't really look at the boot screen, I just assumed it was grub but I believe it was the windows loader...

Anyway, everything's working fine now. Cheers.

---

### Post by Mark Phelps on 2013-11-01
Glad to hear you got it working!

---

