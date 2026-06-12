---
title: "can not boot"
date: 2008-07-10
forum: New to Ubuntu
---

### Post by ccl4 on 2008-07-10
hello,
i have problem with grub when i turn on my comuputer, (i have ubuntu and windows vista). it shows >        [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]

grub> 

 and as followed the re installition of grub it shows > Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"... failed (this is not fatal)
 Running "embed /boot/grub/e2fs_stage1_5 (hd0,6)"... failed (this is not fatal)
 Running "install /boot/grub/stage1 (hd0) /boot/grub/stage2 p /boot/grub/menu.l
st "... failed

Error 22: No such partition

so what should i do??? please help****

---

### Post by Dark_Stang on 2008-07-10
Try re-installing grub from a live cd.
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by ccl4 on 2008-07-10
i did it...

---

### Post by Dark_Stang on 2008-07-10
Oh, sorry. It looks like grub is telling you it can't find that partition. What partition is Ubuntu installed on?

---

### Post by kansasnoob on 2008-07-10
I'm not sure but I wonder if recent Windows updates aren't screwing with GRUB capabilities:confused:

I've had to revert to Vista's boot-loader on three friends computers now to restore their dual-boot capabilities. I don't personally own Vista so I can't just "play" around but I've been using the 4th page of the following tutorial to get their systems working:

[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm)

I dunno?

---

### Post by ccl4 on 2008-07-10
> Disk /dev/sda: 120.0 GB, 120034123776 bytes
129 heads, 4 sectors/track, 454344 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000a6f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               4    14336027     7168012    7  HPFS/NTFS
/dev/sda2   *    14336028   131555747    58609860    7  HPFS/NTFS
/dev/sda3       131555748   225304691    46874472    f  W95 Ext'd (LBA)
/dev/sda4       225304692   234441503     4568406   82  Linux swap / Solaris
/dev/sda5       131555752   196440683    32442466    7  HPFS/NTFS
/dev/sda6       196440688   225304691    14432002   83  Linux


please help!!!

---

### Post by dracayr on 2008-07-10
Well that 
(hd0)

should definitely be sth. like (hd1,1)

EDIT: before typing install, enter root (hd1,1) (if it is in fact 1,1)

You can find out which partition it is by typing:

find /boot/grub/stage1

dracayr

---

### Post by ccl4 on 2008-07-10
>  (hd0,6)!

---

### Post by kansasnoob on 2008-07-10
> **dracayr said:**
> Well that 
(hd0)

should definitely be sth. like (hd1,1)

EDIT: before typing install, enter root (hd1,1) (if it is in fact 1,1)

You can find out which partition it is by typing:

find /boot/grub/stage1

dracayr

How so, with the (hd1,1) that would indicate second hard drive, second partition, eh?

How do you get there?

Maybe I missed something or maybe I'm confused. Guite possible btw:confused:

---

### Post by youthforlinux on 2008-07-10
looks like hd (0,5) to me....just use that find command to figure it out....

---

### Post by kansasnoob on 2008-07-10
> **ccl4 said:**
> !

Now it looks to me like sda6 should boot. Look here:

[http://users.bigpond.net.au/hermanzone/p15.htm#A_Quick_Guide_to_Grubs_Numbering_System](http://users.bigpond.net.au/hermanzone/p15.htm#A_Quick_Guide_to_Grubs_Numbering_System)

---

### Post by kansasnoob on 2008-07-10
> **youthforlinux said:**
> looks like hd (0,5) to me....just use that find command to figure it out....

Please study up on the GRUB numbering guide I just posted!

You're right, I'm tired!

But I doubt that's the problem anyway.

---

### Post by rraj.be on 2008-07-10
I think the Ubuntu Grub should be at (hd0,5)

you can also try for super GRUB Disk.

It will alow you to boot.

just get the iso from here and burn it and use it for booting if you cant solve the problem immediately

```
[linux.softpedia.com/get/System/Boot/Super-Grub-Disk]("linux.softpedia.com/get/System/Boot/Super-Grub-Disk")
```

---

### Post by kansasnoob on 2008-07-10
Twice yesterday I restored GRUB for friends and they came back today with the same problem after booting into Vista. Vista is suddenly not playing at all well with GRUB ............. again!

I suspect it's part of the windows philosophy which appears to be protecting themselves from competition more than protecting their clients from attacks by intruders ................... hell, they've become the intruder!

---

### Post by youthforlinux on 2008-07-11
Well i would try EasyBCD then, it can boot into Ubuntu using the Vista bootloader....

---

