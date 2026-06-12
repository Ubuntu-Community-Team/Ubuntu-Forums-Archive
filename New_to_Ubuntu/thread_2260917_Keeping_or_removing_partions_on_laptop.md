---
title: "Keeping or removing partions on laptop"
date: 2015-01-15
forum: New to Ubuntu
---

### Post by tiamat2009 on 2015-01-15
I have a laptop with windows 8. I don't get windows on dvd to reinstall, so I have made a recovery USB stick as per the manufacturer instructions.

Now I want to replace win 8 with ubuntu, but there are several hidden partions on my laptop: recovery, backup, uefi "something or other".

My queston is, if I want to install ubuntu what partitions should I keep? If I get rid of these extra partitions will be able to still restore everything just using my usb backup of windows 8? Or does that depend on these hidden partitions being there still?

I guess I could leave them there in case I want to go back to windows 8, but if I don't, it seems pointless keeping them and losing that space to something I shall never need.

---

### Post by mastablasta on 2015-01-15
if oyu have external hard disk make an image of the disk using RedoBackup or Clonezilla. The image will include all partitions. Empty space is compressed as well as occupied space. So the image should actually be quite small.

then you can do with original disk anything you want. if you want to return to original setup all you need to do is restore the image to the disk.

---

### Post by Mark Phelps on 2015-01-15
>  I have made a recovery USB stick as per the manufacturer instructions.

The problem with restoring using that is that it is, most likely, a way to restore your PC to original conditions -- BEFORE you installed or configured anything.

My recommendation is to download and install the free edition of Macrium Reflect and use it to image off your PC to an external drive.  You can later use that to restore what you have now.

---

### Post by grahammechanical on 2015-01-15
> [COLOR=#000000]If I get rid of these extra partitions will be able to still restore everything just using my usb backup of windows 8?[/COLOR]

I am not speaking from experience of Windows 8 or UEFI but I doubt the value of getting rid of the UEFI "something or other" partition. You should ask this question: Does the recovery USB makes use of the recovery partition in restoring Windows 8?

If Windows is installed in EFI mode, and Windows 8 usually is, then we must install Ubuntu in EFI mode. I would still install Ubuntu in EFI mode even if I was replacing Windows 8. An EFI "something or other" partition is needed when Ubuntu or Windows is installed in EFI mode.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

And consider this. On this forum I have seen many posts over the years where people say that they have got rid of Windows and now they want it back. And like you they do not have install disks. You might never use Windows again. But the moment we remove it Life will give us a reason for needing to use it. That is life.

Personally, I do not like the idea of paying for an OS that I would not want to use. But having bought the machine and paid for the OS I would not be so quick as to get rid of it.

Regards.

---

### Post by tiamat2009 on 2015-01-15
Thanks for the reply... yes I think I shall keep these samll partitions, I don't have access to the space with windows, so it won't matter it linux can't use the space either.

I have tried sveral live cds/usbs but I always have to put the computer into legacy bios mode... I guess then that that means that it is no longer EFI mode?

---

