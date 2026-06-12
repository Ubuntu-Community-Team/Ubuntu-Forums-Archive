---
title: "formatting XP erased my ubunto :("
date: 2008-10-30
forum: New to Ubuntu
---

### Post by abdelrazzac10 on 2008-10-30
Hi pals,

I have installed UBUNTU on my laptop previously working with windows xp, so I was able to use both xp and ubuntu...xp was on C: drive, and ubuntu was on D: drive... 

I formatted the C: drive and reinstall xp... now there is no ubunto on my laptop!!! I'm sure I didnt format the D: drive by mistake, all data still there, but the laptop boots only on xp!!! it doesnt see ubuntu!!!

I heard something called "Grub" and that I have to reload it... any ideas on what and how to load or reinstall it?

---

### Post by overdrank on 2008-10-30
> **abdelrazzac10 said:**
> Hi pals,

I have installed UBUNTU on my laptop previously working with windows xp, so I was able to use both xp and ubuntu...xp was on C: drive, and ubuntu was on D: drive... 

I formatted the C: drive and reinstall xp... now there is no ubunto on my laptop!!! I'm sure I didnt format the D: drive by mistake, all data still there, but the laptop boots only on xp!!! it doesnt see ubuntu!!!

I heard something called "Grub" and that I have to reload it... any ideas on what and how to load or reinstall it?

Hi and this link may help
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by abdelrazzac10 on 2008-10-30
thank you very much...
I will try to recover ubuntu as soon as possible....

thanks

---

### Post by abdelrazzac10 on 2008-10-31
Hi again,

I have read the different ways to reinstall the grub, but I think that my system is different a bit....

I'm using the first way, Using the Ubuntu Desktop/Live CD, where I open the terminal, write "sudo grub",

then: grub> find /boot/grub/stage1      (and the output is (hd0,7) )

then: grub> root (hd0,1)    (or (hd0,7) I used them both)
then: grub> setup (hd0)
then: grub> quit

but i have the following error: "Error 22: No such partition"

I know that my computer is different a bit... I typed: "fdisk -l" and I had the following outpu:


root@ubuntu:/# fdisk -l
omitting empty partition (5)

Disk /dev/sda: 78.5 GB, 78518522880 bytes
255 heads, 63 sectors/track, 9546 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          10       80293+  de  Dell Utility
/dev/sda2   *          11        4415    35383162+   7  HPFS/NTFS
/dev/sda3            4416        9545    41206725    f  W95 Ext'd (LBA)
/dev/sda4            5946        9545    28916968+   7  HPFS/NTFS
/dev/sda5            4416        4539      995967   82  Linux swap / Solaris
/dev/sda6            4540        4629      722893+  83  Linux
/dev/sda7            4630        5883    10072723+  83  Linux


which means that I have to use sda6 or sda7 instead of hd0...
but I have a different error now: "Error 23: Error while parsing number"


any ideas :(

---

### Post by poldie on 2008-10-31
> **abdelrazzac10 said:**
> Hi pals,

I have installed UBUNTU on my laptop previously working with windows xp, so I was able to use both xp and ubuntu...xp was on C: drive, and ubuntu was on D: drive... 

I formatted the C: drive and reinstall xp... now there is no ubunto on my laptop!!! I'm sure I didnt format the D: drive by mistake, all data still there, but the laptop boots only on xp!!! it doesnt see ubuntu!!!

I heard something called "Grub" and that I have to reload it... any ideas on what and how to load or reinstall it?

I've got used to physically removing (unplugging the power lead from) other hard drives in a system when installing XP as twice I did it this year to one drive and another drive on the other IDE channel ended up `unintialised` both times.   I believe it's a bug in the MS installer - I can't think of any other possibility.  You only install to one drive at a time, so I don't see how this could have happened even if I'd wanted it to.

---

### Post by Elfy on 2008-10-31
The drives number like this for grub 

[http://users.bigpond.net.au/hermanzone/p15.htm#A_Quick_Guide_to_Grubs_Numbering_System](http://users.bigpond.net.au/hermanzone/p15.htm#A_Quick_Guide_to_Grubs_Numbering_System)

you need to find out which is which though sda6 or sda7 :)

---

### Post by abdelrazzac10 on 2008-10-31
> **forestpixie said:**
> The drives number like this for grub 

[http://users.bigpond.net.au/hermanzone/p15.htm#A_Quick_Guide_to_Grubs_Numbering_System](http://users.bigpond.net.au/hermanzone/p15.htm#A_Quick_Guide_to_Grubs_Numbering_System)

you need to find out which is which though sda6 or sda7 :)


but I have tried setup with sda6 and sda7 but both didnt give me any solution!!!

and because I'm using a laptop....... I don't think I'm able to unplug my hard disks

---

### Post by Elfy on 2008-10-31
yopu don't use sdxy in grub you must use hdxy

---

