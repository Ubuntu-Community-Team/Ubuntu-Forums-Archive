---
title: "Dual Booting Questions"
date: 2008-11-11
forum: New to Ubuntu
---

### Post by Airforcefalco on 2008-11-11
I would like to put my copy of Windows back on my laptop but I want to make sure that I don't mess up the Linux installation. 

I heard that you can use the commands dd and gzip in GRUB to compress the OS to conserve space, does anyone know how to do this?

---

### Post by louieb on 2008-11-11
A bunch of how to dual boot this or that with that or this installed first. [apc HowTo dual boot]("http://apcmag.com/howto_category.htm?cid=198")

you can use dd and gzip to backup an OS. Don't believe you can boot to a compressed OS.

---

### Post by Airforcefalco on 2008-11-11
Not boot to a compressed OS but compress an OS until you want to boot to it and then decompress.

---

### Post by caljohnsmith on 2008-11-11
If you want to compress your OS, you could compress the entire partition with:
```
sudo dd if=/dev/[COLOR="Blue"]<partition>[/COLOR] bs=10M conv=notrunc,noerror | gzip -c > ~/Desktop/OS_backup.gz
```
And replace <partition> with the OS partition, like sda1. To expand it and put it back:
```
zcat ~/Desktop/OS_backup.gz | dd of=/dev/[COLOR="Blue"]<partition[/COLOR]> bs=10M conv=notrunc,noerror
```
And of course make sure you get <partition> correct or you could cause yourself some big trouble. :)

---

### Post by Slug71 on 2008-11-11
Windows has to be the first partition on your Harddrive.

---

### Post by Airforcefalco on 2008-11-11
> **Slug71 said:**
> Windows has to be the first partition on your Harddrive.

I read that you could use GRUB to handle it.

---

### Post by Paqman on 2008-11-11
Linux doesn't take up a lot of space. You should be able to shrink it's partition(s) down quite small and still have them work fine. Gparted will tell you how much space on a partition is actually in use before you make any changes.

---

### Post by caljohnsmith on 2008-11-11
> **Slug71 said:**
> Windows has to be the first partition on your Harddrive.
Fortunately, that is not true. You can install Windows to any primary partition, and in fact you can even install Windows to a logical partition if there is a NTFS/FAT primary partition available where Windows can put its boot files. If you want some examples of people who have Windows on a different partition than the first one, here are some examples:

[http://ubuntuforums.org/showthread.php?t=955671](http://ubuntuforums.org/showthread.php?t=955671)
[http://ubuntuforums.org/showthread.php?t=953444](http://ubuntuforums.org/showthread.php?t=953444)
[http://ubuntuforums.org/showthread.php?t=952045](http://ubuntuforums.org/showthread.php?t=952045)
[http://ubuntuforums.org/showthread.php?t=952048](http://ubuntuforums.org/showthread.php?t=952048)
[http://ubuntuforums.org/showthread.php?t=936866](http://ubuntuforums.org/showthread.php?t=936866)
[http://ubuntuforums.org/showthread.php?t=940285](http://ubuntuforums.org/showthread.php?t=940285)
[http://ubuntuforums.org/showthread.php?t=964779](http://ubuntuforums.org/showthread.php?t=964779)
[http://ubuntuforums.org/showthread.php?p=6096278](http://ubuntuforums.org/showthread.php?p=6096278)

---

### Post by handydan918 on 2008-11-11
> **Airforcefalco said:**
> I would like to put my copy of Windows back on my laptop but I want to make sure that I don't mess up the Linux installation. 
Well, you WILL mess up your Ubu install....at least, the bootloader, GRUB.  Just reinstall grub after you reinstall Windows. > 
I heard that you can use the commands dd and gzip in GRUB to compress the OS to conserve space, does anyone know how to do this?

Why would you want to do this? How small is you disc?

---

### Post by Airforcefalco on 2008-11-11
> **handydan918 said:**
> Why would you want to do this? How small is you disc?

Well it is 250 GB.

The reasons I want to do this is because eventually I would like to try different versions of Linux and Windows. I have XP and my laptop came with Vista so I want to conserve as much space as I can for family videos and pictures. I really just want to experiment and that suggestion sounded kind of fun.

---

### Post by ichi@YUKI on 2008-11-11
> **Slug71 said:**
> Windows has to be the first partition on your Harddrive.

I have to agree on this one. Windows hates it if another OS has been installed before it. I tried both the dual-booting windows first and ubuntu first. It seems the latter can cause much of a headache.

---

### Post by hellion0 on 2008-11-11
Whatever you do, snag a copy of the Super Grub Disc. It'll help you out, since installing Windows will wipe out your present bootloader.

---

### Post by Paqman on 2008-11-11
> **Airforcefalco said:**
> 
The reasons I want to do this is because eventually I would like to try different versions of Linux and Windows.

A Linux distro is quite happy with 10GB, so you could try out quite a few simultaneously on a 250Gb drive.

If you create a separate /home partition you can share it between any number of distros (just create separate users for each distro) Once you've got /home separated you could probably squeeze most distros onto 6-8GB without much hassle. Having said that, I give them 20GB since i've got plenty of space (WinXP/Ubuntu on a 160GB drive)

---

### Post by Airforcefalco on 2008-11-11
Does anyone know how to do this?

---

