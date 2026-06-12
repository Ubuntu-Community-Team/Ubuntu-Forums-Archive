---
title: "Dualboot Grub WinXP"
date: 2008-08-15
forum: New to Ubuntu
---

### Post by nemtaro on 2008-08-15
I realize that similar questions have been asked before. However, I've been searching for a couple of hours and can't figure out what the problem is:

fdisk -l output:
```
Disk /dev/sda: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xee3abb7b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               2       14203   114077565    f  W95 Ext'd (LBA)
/dev/sda2   *       14204       14946     5968147+  83  Linux
/dev/sda5               2       14162   113748201    b  W95 FAT32
/dev/sda6           14163       14203      329301   82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbb66bb66

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9728    78140128+   7  HPFS/NTFS

```

grub.lst entry:
```
title		Microsoft Windows XP Professional
root		(sdb1,0)
savedefault
makeactive
chainloader	+1

```

I'm getting a "Error 23: Error while parsing number." msg when trying to boot
from the windows option. 

XP is on the 80GB hard disk.
What am I doing wrong? 

Thanks!

---

### Post by Gannon8 on 2008-08-15
> **nemtaro said:**
> grub.lst entry:
```
title		Microsoft Windows XP Professional
root		[COLOR="Red"](sdb1,0)[/COLOR]
savedefault
makeactive
chainloader	+1

```
Should be:
```
title		Microsoft Windows XP Professional
root		[COLOR="Red"](hd1,0)[/COLOR]
savedefault
makeactive
chainloader	+1
```
GRUB does not use /dev/ style of naming it's hard drives. The first one is (hd0), the second one is (hd1). First partition of first hard drive is (hd0,0), second is (hd0,1).

---

### Post by nemtaro on 2008-08-15
Thanks for your very quick response!

I'm guessing that it now tries to boot from XP, but I'm getting this error msg: 

```
Starting up....

Invalid System disk
Replace the disk and then press any key.
DISK BOOT FAILURE, INSERT SYSTEM DISK AND PRESS RETURN
```

If I change my BIOS boot disk priority so that the 80GB disk is first, XP will load fine. At the moment, the 120GB drive is in boot priority and Grub is on this disk. 

Any suggestions?

---

### Post by mrtomservo on 2008-08-15
I found some info on this page for Gentoo, seems similar to what you're describing.  

[http://www.gentoo.org/doc/en/grub-error-guide.xml]("http://www.gentoo.org/doc/en/grub-error-guide.xml")

> 16.  Failing To Boot Windows From a Second Harddrive

Situation

After selecting the Windows entry, the system refuses to boot without any clear reason as to why.

Solution

cyrillic informed us that you can "map" your disks in a different order by changing your grub.conf's Windows entry like so:

Code Listing 16.1: Mapping disks

title Windows XP
  map (hd0) (hd1)
  map (hd1) (hd0)
  chainloader (hd1,0)+1


---

### Post by kansasnoob on 2008-08-15
> **nemtaro said:**
> I realize that similar questions have been asked before. However, I've been searching for a couple of hours and can't figure out what the problem is:

fdisk -l output:
```
Disk /dev/sda: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xee3abb7b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               2       14203   114077565    f  W95 Ext'd (LBA)
/dev/sda2   *       14204       14946     5968147+  83  Linux
/dev/sda5               2       14162   113748201    b  W95 FAT32
/dev/sda6           14163       14203      329301   82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbb66bb66

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9728    78140128+   7  HPFS/NTFS

```

grub.lst entry:
```
title		Microsoft Windows XP Professional
root		(sdb1,0)
savedefault
makeactive
chainloader	+1

```

I'm getting a "Error 23: Error while parsing number." msg when trying to boot
from the windows option. 

XP is on the 80GB hard disk.
What am I doing wrong? 

Thanks!


Gosh, sda2, which appears to be your Linux OS looks really small from that.

Could you post an actual screenshot of the drive? That would require using gparted (aka, partition editor) and I'm not sure how you're posting.

It's part of the live CD, but if you're able to run your mounted Ubuntu OS then you'd have to install it

---

### Post by Gannon8 on 2008-08-15
> **kansasnoob said:**
> Gosh, sda2, which appears to be your Linux OS looks really small from that.

Could you post an actual screenshot of the drive? That would require using gparted (aka, partition editor) and I'm not sure how you're posting.

It's part of the live CD, but if you're able to run your mounted Ubuntu OS then you'd have to install it
That does not seem to be his problem. His problem is that he cannot boot Windows off a second hard drive.

---

### Post by nemtaro on 2008-08-15
mrtomservo: with the following grub.lst entry it prints "Starting up...." and goes idle with no hdd activity.

```
title		Microsoft Windows XP Professional
map (hd1) (hd0)
map (hd0) (hd1)
chainloader (hd0,0)+1
```

using the original entry from the gentoo page resulted in the same error as before.

kansasnoob: I'm actually posting from Ubuntu, and I'm able to run XP by changing the BIOS boot disk priority. I'm trying to figure out Grub so I don't have to continue doing that. The small partition size for Ubuntu is fine with me because I only use it as a dev environment. 

Any other suggestions would be appreciated.

---

### Post by Too Late on 2008-08-15
I think there must always be a 'root (hd...)' line below the title line. Also, the chainloader command probably doesn't need anything else that +1.

So try this:```

title Microsoft Windows XP Professional
root (hd1,0)
map (hd1) (hd0)
map (hd0) (hd1)
chainloader +1
```

---

### Post by mrtomservo on 2008-08-15
Hmmm.  Well, i'm running out of ideas, but you could try doing a bit of research on this file regarding grub: /boot/grub/device.map.  I guess my ultimate point would be that if it works when you trick your pc into thinking the second drive is first with the bios, there has to be a way to do the same in grub.

---

### Post by nemtaro on 2008-08-15
TooLate: 

```
title		Microsoft Windows XP Professional
root (hd1,0)
map (hd1) (hd0)
map (hd0) (hd1)
chainloader +1
```

resulted in the same error:
```
Starting up....

Invalid System disk
Replace the disk and then press any key.
DISK BOOT FAILURE, INSERT SYSTEM DISK AND PRESS RETURN
```

But it did run the map commands because after going back into grub, Ubuntu (on hd0) wouldn't load anymore without a reboot.

Sigh, desperation grows.

---

### Post by kansasnoob on 2008-08-15
Well look at this:

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

But basically I think you have a situation where the BIOS is looking one place for Grub and it's on a different drive. 

Also look at Herman's grub page:

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by Gannon8 on 2008-08-15
I don't think you should use the map commands after the root command. Try:
```
title		Microsoft Windows XP Professional
map (hd1) (hd0)
map (hd0) (hd1)
root (hd1,0)
chainloader +1
```

---

### Post by caljohnsmith on 2008-08-15
Can you go into BIOS and change your HDD boot order so that your computer will boot your sdb Windows drive? I think most computers now allow you to hit F12 on startup to temporarily choose which device to boot off of. That will tell you whether Windows is even still bootable, or whether it is a problem with booting from Grub.

If Windows isn't bootable, I would give fixing the MBR on your Windows HDD a shot. Try booting up your Windows Install CD, go into recovery mode, and then run:
```
fixmbr
fixboot
```

---

### Post by Too Late on 2008-08-15
> **Gannon8 said:**
> I don't think you should use the map commands after the root command. Try:
```
title		Microsoft Windows XP Professional
map (hd1) (hd0)
map (hd0) (hd1)
root (hd1,0)
chainloader +1
```
You're right. I forgot that because I had the makeactive command between the map and chainloader commands in my file, and that does the same thing (if that partition has a bootable flag).

---

### Post by louieb on 2008-08-15
> **Gannon8 said:**
> I don't think you should use the map commands after the root command. Try:
```
title        Microsoft Windows XP Professional
map (hd1) (hd0)
map (hd0) (hd1)
root (hd1,0)
chainloader +1
```

+1 I have 2 IDE drives XP is on the slave. That is what my XP entry looks like.
With one exception I use [COLOR=Red]**rootnoverify (hd1,0) ** [COLOR=Black]instead of root (hd0,1). But seem to remember either should work.[/COLOR][/COLOR]

---

### Post by nemtaro on 2008-08-15
> **Gannon8 said:**
> I don't think you should use the map commands after the root command. Try:


Tried that.
```
title		Microsoft Windows XP Professional
map (hd1) (hd0)
map (hd0) (hd1)
root (hd1,0)
chainloader +1
``` Gives the "Invalid System Disk" error. and 
```
title		Microsoft Windows XP Professional
map (hd1) (hd0)
map (hd0) (hd1)
root [COLOR="Red"](hd0,0)[/COLOR]
chainloader +1
``` Goes idle after printing "Starting up..."

caljohnsmith: I just tried setting BIOS to load sdb1 first and Windows boots up fine. My BIOS doesn't have an F12 bootloader, if it did, I'd get rid of Grub all together. 

It might not matter, but Ubuntu is on an IDE drive, and XP is on a SATA drive. I'll try rootnoverify and post back.

---

### Post by nemtaro on 2008-08-15
rootnoverify gave the same results.

> **Gannon8 said:**
> Should be:
GRUB does not use /dev/ style of naming it's hard drives. The first one is (hd0), the second one is (hd1). First partition of first hard drive is (hd0,0), second is (hd0,1).

I should've paid more attention to this. Here is my complete fdisk -l output:
```
Disk /dev/sda: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xee3abb7b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               2       14203   114077565    f  W95 Ext'd (LBA)
/dev/sda2   *       14204       14946     5968147+  83  Linux
/dev/sda5               2       14162   113748201    b  W95 FAT32
/dev/sda6           14163       14203      329301   82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbb66bb66

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9728    78140128+   7  HPFS/NTFS

Disk /dev/sdc: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1bebd24d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       24793   199149741    c  W95 FAT32 (LBA)

Disk /dev/sdd: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x32744584

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       36484   293057698+   7  HPFS/NTFS

```

Now, how can I figure out what hd# in Grub refers to sdb1 ?

---

### Post by caljohnsmith on 2008-08-15
I wish you would have posted your full fdisk output before, because that explains it: unfortunately, Grub does not always see the order of your HDDs as the same as BIOS. 

How about going into the Grub CLI and doing:
```
sudo grub
grub> geometry (hd0)
grub> geometry (hd1)
grub> geometry (hd2)
grub> geometry (hd3)
```
Based on the results you get from the commands, I think you will be able to figure out which Grub (hdX) corresponds to your /dev/sdX. If it isn't clear though, go ahead and post the results and we'll give you a hand sorting it out. :)

---

### Post by kansasnoob on 2008-08-15
[http://users.bigpond.net.au/hermanzone/p15.htm#Chainloading_Windows_using_map_commands](http://users.bigpond.net.au/hermanzone/p15.htm#Chainloading_Windows_using_map_commands)

---

### Post by nemtaro on 2008-08-15
Sorry about that caljohnsmith:
```
grub> geometry (hd0)
drive 0x80: C/H/S = 14946/255/63, The number of sectors = 240121728, /dev/sda
   Partition num: 1,  Filesystem type is ext2fs, partition type 0x83
   Partition num: 4,  Filesystem type is fat, partition type 0xb
   Partition num: 5,  Filesystem type unknown, partition type 0x82

grub> geometry (hd1)
drive 0x81: C/H/S = 9729/255/63, The number of sectors = 156301488, /dev/sdb
   Partition num: 0,  Filesystem type unknown, partition type 0x7

grub> geometry (hd2)
drive 0x82: C/H/S = 24792/255/63, The number of sectors = 398297088, /dev/sdc
   Partition num: 0,  Filesystem type is fat, partition type 0xc

grub> geometry (hd3)
drive 0x83: C/H/S = 36483/255/63, The number of sectors = 586114704, /dev/sdd
   Partition num: 0,  Filesystem type unknown, partition type 0x7

```

My understanding is that (hd1,0) is sdb1 and (hd0,1) is sda2. Meaning the previous setting should have worked.

Is that correct?

---
Instead of rebooting every time, I tried running the map and chainloader commands in the grub CLI: 
```
grub> map (hd0) (hd1)

grub> map (hd1) (hd0)

grub> chainloader +

Error 12: Invalid device requested

```

kansasnoob: I didn't ignore your post. I just can't figure out if my current menu.lst entry is different from what the guide is suggesting.

Should I nuke Ubuntu and start a clean install on the same drive that windows is on?

---

### Post by caljohnsmith on 2008-08-15
According to your geometry outputs, it looks like you're lucky and Grub actually does see your HDDs in the same order as BIOS does, meaning that (hd1,0) should correspond to sdb1 like you thought. But since you are still getting an error booting Windows even with the correct mapping commands in Grub, this error can happen if the IDE and SATA drives are not setup properly in BIOS (if I remember correctly). I wish I could give you a link of exactly how to fix it, but unfortunately I didn't save the URLs when I came across that info since I don't have that problem.

Also, as one last check of your Grub's configuration, would you please post the contents of your /boot/grub/device.map? If the device mapping in that file is OK, then I think you're problem is most likely with your BIOS HDD settings.

---

### Post by nemtaro on 2008-08-15
device.map file contents:
```
(hd0)	/dev/sda
(hd1)	/dev/sdb
(hd2)	/dev/sdc
(hd3)	/dev/sdd

```
Should I change this file?

That's interesting caljohnsmith. Do you remember if you had to manually configure your hard drives in BIOS?
At the moment my SATA and IDE connections are all set to Auto and the ones not in use are set to None to avoid checking on reboot.

Other than that, we think the following Grub config should work, right? 
```
title		Microsoft Windows XP Professional
map (hd1) (hd0)
map (hd0) (hd1)
root (hd0,0)
chainloader +1
```

I appreciate all you guys help!

---

### Post by caljohnsmith on 2008-08-16
> ```
title		Microsoft Windows XP Professional
map (hd1) (hd0)
map (hd0) (hd1)
root [COLOR="Red"](hd0,0)[/COLOR]
chainloader +1
```
Actually, I think you have a small typo--the (hd0,0) should be (hd1,0). :)

You're device.map is just as it should be, or I should say at least it has Grub's default mapping at this point. I think your best bet at this point is to just try all three possibilities since it is not clear (at least to me, maybe someone else knows) why (hd1,0) isn't working. Try putting the following in your menu.lst, and see which one works. By the way, having the root entry before or after the mapping entries makes no difference at least in my experience. Also, I've found that the "makeactive" line doesn't seem to be necessary to boot my Windows XP, but in the Grub manual they recommend using it with the Windows operating system, so I don't argue with them. :)
```
title		Windows XP (hd1,0)
root		(hd1,0)
makeactive
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader	+1

title		Windows XP (hd2,0)
root		(hd2,0)
makeactive
map             (hd0) (hd2)
map             (hd2) (hd0)
chainloader	+1

title		Windows XP (hd3,0)
root		(hd3,0)
makeactive
map             (hd0) (hd3)
map             (hd3) (hd0)
chainloader	+1
```
And if for some reason even the above doesn't work, you could try booting the HDD itself from Grub instead of directly booting the Windows partition on that HDD; this should work since you said you were able to boot your Windows HDD (sdb) by changing the BIOS boot order, so your MBR must be fine on your Windows HDD. To boot the HDDs (i.e. let Grub hand off the booting process to the HDD's MBR), try the following:
```
title		(hd1,0)
root		(hd1)
chainloader	+1

title		(hd2,0)
root		(hd2)
chainloader	+1

title		(hd3,0)
root		(hd3)
chainloader	+1
```

---

### Post by nemtaro on 2008-08-16
Very strange indeed:
```
title             Windows XP (hd1,0)
```
would just go idle after printing "Starting up..."

```
title		Windows XP (hd2,0)
and 
title		Windows XP (hd3,0)
```
both give a "NTLDR Missing, Press any key to restart" error

and ```
title		(hd1,0)
``` gives a "NTLDR Missing, Press Ctrl+Alt+Delete to restart" error

I think I'll just backup my windows partition, and reinstall Ubuntu on the same hard drive that windows is on.

Thanks for your time caljohnsmith!

---

