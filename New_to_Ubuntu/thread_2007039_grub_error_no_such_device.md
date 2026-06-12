---
title: "grub error no such device"
date: 2012-06-20
forum: New to Ubuntu
---

### Post by namanahuja on 2012-06-20
i have a hp netbook which came with a preinstalled copy win7untu 
i had installed ubuntu12.04 through WUBI. Yesterday after installing BURG i was not able to boot, folling error appears:

error: no such device:e4635099-89df-4538-8a43-cefac4a53b3
Entering rescue mode...
grub rescue>

---

### Post by carl4926 on 2012-06-20
wubi
is not a real installation

is that what you intended?

---

### Post by Shadius on 2012-06-20
It is advised not to install BURG when you have a WUBI installation, according to the [WUBI Megathread]("http://ubuntuforums.org/showthread.php?t=1639198"). I suggest you check there for all your WUBI related problems.

I would look at Problem #1. Solution #2 is probably the easiest, especially if you don't have the Windows Recovery CD.

---

### Post by wilee-nilee on 2012-06-20
> **namanahuja said:**
> i have a hp netbook which came with a preinstalled copy win7untu 
i had installed ubuntu12.04 through WUBI. Yesterday after installing BURG i was not able to boot, folling error appears:

error: no such device:e4635099-89df-4538-8a43-cefac4a53b3
Entering rescue mode...
grub rescue>

You need to reload the windows bootloader to the mbr, what version of windows is this and do you have a recovery or install disc?

I can't gaurantee the wubi will show, but we can get windows back.

---

### Post by namanahuja on 2012-06-20
> **wilee-nilee said:**
> You need to reload the windows bootloader to the mbr, what version of windows is this and do you have a recovery or install disc?

I can't gaurantee the wubi will show, but we can get windows back.

its a windows 7 SP 1. dont have recovery disk but hp recovery[which also cant be booted to ], loosing wubi is not a problem at all

---

### Post by Shadius on 2012-06-20
> **namanahuja said:**
> its a windows 7 SP 1. dont have recovery disk but hp recovery[which also cant be booted to ], loosing wubi is not a problem at all

You mean the HP Recovery Manager program that came installed on Windows 7, correct?

---

### Post by wilee-nilee on 2012-06-20
> **namanahuja said:**
> its a windows 7 SP 1. dont have recovery disk but hp recovery[which also cant be booted to ], loosing wubi is not a problem at all

You can make a recovery disc in the windows backup and restore, do it immediately once we get you in. If you had done that we would not have to do this.

You need a live ubuntu cd, we can install a bootloader that will boot windows called lilo. Boot the cd and follow these directions.

                                  [FONT=Verdana, sans-serif][SIZE=1]Restore basic windows boot loader - universe enabled [/SIZE][/FONT] 
 [FONT=Verdana, sans-serif][SIZE=1]open ubuntu software center-edit-software sources, first tab, tick universe, close those windows and open a terminal, and run these commands [/SIZE][/FONT] 
 [FONT=Verdana, sans-serif][SIZE=1]sudo apt-get update [/SIZE][/FONT] 
 [FONT=Verdana, sans-serif][SIZE=1]sudo fdisk -l   (confirms hd=sdX, and windows partitions) [/SIZE][/FONT] 
 [FONT=Verdana, sans-serif][SIZE=1]sudo apt-get install lilo [/SIZE][/FONT] 
 [FONT=Verdana, sans-serif][SIZE=1]sudo lilo -M /dev/sda mbr [/SIZE][/FONT] 
 **[FONT=Verdana, sans-serif][SIZE=1]May show error messages about the rest of lilo missing, ignore, we just want MBR [/SIZE][/FONT]**

---

### Post by namanahuja on 2012-06-20
> **wilee-nilee said:**
> You can make a recovery disc in the windows backup and restore, do it immediately once we get you in. If you had done that we would not have to do this.

You need a live ubuntu cd, we can install a bootloader that will boot windows called lilo. Boot the cd and follow these directions.

                                  [FONT=Verdana, sans-serif][SIZE=1]Restore basic windows boot loader - universe enabled [/SIZE][/FONT] 
 [FONT=Verdana, sans-serif][SIZE=1]open ubuntu software center-edit-software sources, first tab, tick universe, close those windows and open a terminal, and run these commands [/SIZE][/FONT] 
 [FONT=Verdana, sans-serif][SIZE=1]sudo apt-get update [/SIZE][/FONT] 
 [FONT=Verdana, sans-serif][SIZE=1]sudo fdisk -l   (confirms hd=sdX, and windows partitions) [/SIZE][/FONT] 
 [FONT=Verdana, sans-serif][SIZE=1]sudo apt-get install lilo [/SIZE][/FONT] 
 [FONT=Verdana, sans-serif][SIZE=1]sudo lilo -M /dev/sda mbr [/SIZE][/FONT] 
 **[FONT=Verdana, sans-serif][SIZE=1]May show error messages about the rest of lilo missing, ignore, we just want MBR [/SIZE][/FONT]**

no optical drive in NETBOOK

---

### Post by carl4926 on 2012-06-20
You can use 'dd' or unetbootin to write ubuntu to a flash drive

---

### Post by wilee-nilee on 2012-06-20
> **namanahuja said:**
> no optical drive in NETBOOK

Then use a usb flash, use unetbootin or another usb loader app to load it.

---

### Post by Shadius on 2012-06-20
> **namanahuja said:**
> no optical drive in NETBOOK

No worries. Use a [LiveUSB]("http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows")

---

### Post by namanahuja on 2012-06-20
> **Shadius said:**
> You mean the HP Recovery Manager program that came installed on Windows 7, correct?

yes can it help?

---

### Post by namanahuja on 2012-06-20
> **wilee-nilee said:**
> You need to reload the windows bootloader to the mbr, what version of windows is this and do you have a recovery or install disc?

I can't gaurantee the wubi will show, but we can get windows back.

hey i just remembere i have a partition D which is a recovery partition if it can help

---

### Post by Shadius on 2012-06-20
> **namanahuja said:**
> yes can it help?

As wilee-nilee said, it would've been beneficial to you if you had created the recovery CDs beforehand. The HP Recovery Manager helps you create those CDs. I also suggest you create those recovery CDs once you recover your Windows 7. Please follow wilee-nilee's previous post after you've created the LiveUSB.

---

### Post by namanahuja on 2012-06-20
> **Shadius said:**
> As wilee-nilee said, it would've been beneficial to you if you had created the recovery CDs beforehand. The HP Recovery Manager helps you create those CDs. I also suggest you create those recovery CDs once you recover your Windows 7. Please follow wilee-nilee's previous post after you've created the LiveUSB.
is there a way to reset to factory default or something like that?

---

### Post by namanahuja on 2012-06-20
> **wilee-nilee said:**
> You need to reload the windows bootloader to the mbr, what version of windows is this and do you have a recovery or install disc?

I can't gaurantee the wubi will show, but we can get windows back.
is there a way to reset to factory default or something like that?

---

### Post by wilee-nilee on 2012-06-20
> **namanahuja said:**
> is there a way to reset to factory default or something like that?

Not from a grub>

You really only have one choice here, without the recovery disc, which you can buy from the web.
[http://systemdiscs.com/?utm_source=neosmart&utm_medium=article&utm_campaign=Win7_Recovery](http://systemdiscs.com/?utm_source=neosmart&utm_medium=article&utm_campaign=Win7_Recovery)

Or if you can get a install or recovery disc from a friend.

You have backed yourself into a corner without the proper tools, and have been given the answer to fix this.

---

### Post by Shadius on 2012-06-20
> **namanahuja said:**
> is there a way to reset to factory default or something like that?

The Recovery CD would give you that option and so you know, that would return your computer to factory settings, deleting all your current data. Once you get back your Windows 7 by creating the LiveUSB and following wilee-nilee's post, you can access the HP Recovery Manager and restore your computer to factory settings.

---

### Post by YannBuntu on 2012-06-20
> **namanahuja said:**
> i have a hp netbook which came with a preinstalled copy win7untu 
i had installed ubuntu12.04 through WUBI. Yesterday after installing BURG i was not able to boot, folling error appears:

error: no such device:e4635099-89df-4538-8a43-cefac4a53b3
Entering rescue mode...
grub rescue>

Please could you indicate your [BootInfo URL]("http://ubuntuforums.org/showpost.php?p=11136267&postcount=1")?

---

