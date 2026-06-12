---
title: "Need to boot into Vista (Broken GRUB)"
date: 2008-05-26
forum: New to Ubuntu
---

### Post by Heathtech on 2008-05-26
Hello!

Here's the basic info:
A while back I installed Ubuntu 7.04 from a liveCD.  It installed perfectly and I had fun from there (Beryl, etc.)  I tried to upgrade to 7.10, but while it was upgrading it had some problems and caused the Ubuntu to crash upon loading.
Recently, I went into my Windows Disk Manager thing to remove the Ubuntu partition.  I did so, but I made the mistake of changing it to the Windows partition and leaving only 500MB as "Free Space."  When I rebooted some time later, my GRUB loader came up with the welcoming message of "Error 17."
Now I am forced to use my original liveCD so that I could try to sort something out, but to no avail.  I would like to keep the GRUB loader, but I cannot modify the config file because it apparently doesn't exist anymore (hence the error 17, probably.)

I even tried to make a boot floppy disk, but when I use 'fdformat /dev/sdb' it says "Could not determine current format type: Invalid argument."  Using a different instruction, I tried to make the boot floppy disk, but when I restarted the computer, it said something like "Operating System not found."

I hope your answers aren't too harsh.  I chose this forum "Absolute Beginner Talk" because I know very little on how Ubuntu or GRUB work.
Thanks in advance for any help you can offer.  If you need more info, I can give it.

---

### Post by forestpixie on 2008-05-26
You can just use your xp disc to fixmbr it will then boot windows - why do you want to use grub?

If you haven't got an xp disc you can use supergrub to fix the win mbr

---

### Post by Maestro23 on 2008-05-26
Edit. Already answered.

---

### Post by Heathtech on 2008-05-26
The idiots (HP) who created the recovery discs screwed up because when I put in my recovery DVD it says that my PC is not compatible with the recovery module on the disc.  Anyway, I wanted to keep grub because I want to reinstall Ubuntu some time.  I guess it would install anyway, but that seems like a silly question.

As for the Super Grub, I can't use the floppy one because fd0 doesn't exist (Since it is a USB drive) and the sdb doesn't work either.  I'm resorting to the USB pendrive one since it says that it won't affect any of the files on it.  I already knew about super grub disk, but I didn't know it had the USB solution until I checked again.  I hope it works.  Thanks.

If it doesn't work, I'll put more feedback below:
(edit) I tried to follow their instructions, but while I was trying to adjust the GRUB settings, I got three different GRUB error messages.  I think they were 21, 17, and 18 but I don't remember.  There was mention that there might be error messages so I tried booting anyway.  When it booted, it said "Invalid Drive System Specified" or something along those lines...

I hope someone can give some more help...

(EDIT2) Tried again after re-partitioning my flashdrive and now I get Errors 15, 21, and 12 with GRUB.  I'm going to try booting again, but I don't think it'll help.

---

### Post by meierfra. on 2008-05-26
Boot from the Ubuntu LiveCD and give "ms-sys" a try: Click on FixMBR  in my signature and look for the  3rd method.

---

### Post by rajaram_s on 2008-05-26
Fo u have a seperate partition for /boot?

---

### Post by adrian15 on 2008-05-27
> **Heathtech said:**
> I already knew about super grub disk, but I didn't know it had the USB solution until I checked again.  I hope it works.  Thanks.

If it doesn't work, I'll put more feedback below:
(edit) I tried to follow their instructions, but while I was trying to adjust the GRUB settings, I got three different GRUB error messages.  I think they were 21, 17, and 18 but I don't remember.  There was mention that there might be error messages so I tried booting anyway.  When it booted, it said "Invalid Drive System Specified" or something along those lines...

I hope someone can give some more help...

(EDIT2) Tried again after re-partitioning my flashdrive and now I get Errors 15, 21, and 12 with GRUB.  I'm going to try booting again, but I don't think it'll help.

How did you repartition it? The errors happen at trying to reinstall grub to SGD usb? When trying to boot the usb? When trying to boot your Linux from SGD menues?

Can you copy-paste exactly the steps you are doing?

adrian15

---

