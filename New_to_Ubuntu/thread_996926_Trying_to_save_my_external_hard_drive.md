---
title: "Trying to save my external hard drive"
date: 2008-11-29
forum: New to Ubuntu
---

### Post by swarup on 2008-11-29
I have a 150 GB external Maxtor HD, and the other day my colleague had it connected to a computer that was running Vista, and the external HD got disconnected before the computer was completely turned off. As a result, the HD is now acting dysfunctionally. It is no longer recognized by Vista. When I hook it up to an Ubuntu machine, it says the drive is not mountable. But if I open Ubuntu's Partition Editor, then it recognizes the drive just fine and shows it. In the Partition Editor I can select the drive, and can format it to any system -- ext3, NTFS, FAT32. But regardless of what I format it as, Ubuntu will not mount it. And finally, I have an XP machine which recognizes it just fine (if I have it formatted by GParted as NTFS). In the XP machine I can copy files to the drive, can open the files, and when I put programs on the drive I can open and run those too. But in XP's disk management, it lists the drive as bad, and will not format it.

I thought it would be good to write zero's to the drive and do a slow format. I have Hiren's boot disk, but as far as I understand that is only for working on a computer's own internal boot drive, and is not for an external HD.


Can you suggest to me what I can do to get this Maxtor external HD fully functional again?

---

### Post by taurus on 2008-11-29
Plug the drive into your machine and post the output of these commands from a terminal.

```
dmesg | tail 
sudo fdisk -l
```

---

### Post by Olivier2371 on 2008-11-29
Hello there,

If you want to zero your drive, I would recommend you to use the maxtor tool

call "Maxblast".

I put the link where you can download it.

[http://www.seagate.com/ww/v/index.jsp?locale=en-US&name=MaxBlast_5&vgnextoid=7add8b9c4a8ff010VgnVCM100000dd04090aRCRD]("http://www.seagate.com/ww/v/index.jsp?locale=en-US&name=MaxBlast_5&vgnextoid=7add8b9c4a8ff010VgnVCM100000dd04090aRCRD")

just create a start up disk, boot from it then follow the instruction.

Make sure your usb disk is plugged in.

I hope this is helpful.

---

### Post by nebu on 2008-11-29
after you formatted your drive.... did u check to see if it works on vista???


as far as understand.... your filesystem had become corrupt.....

try fixing it with ntfsfix.....

ull have to install it with....

> sudo apt-get install ntfsprogs

and then run it with...

> sudo ntfsfix /dev/hda*

hda*/sda* will be the hard disk you want to check


u can do the same in widows with

chkdsk <Disk>:/f

<Disk> is the alphabet windows allots to your disk

---

### Post by o.besner on 2008-11-29
you can force the hard drive to mount, since gnome won't mount a hard-drive in ntfs that was shutdown inapropriately.

I recommend doing the ntfsfix mentionned above first

Then open a console and type 

```
sudo ntfs-3g /dev/yourharddrive /your/favorite/mountpoint -o force
```

for example,my hard drive (called MisterT) would be mounted this way :

sudo ntfs-3g /dev/sdb1 /windows/MisterT -o force

---

### Post by swarup on 2008-11-29
> **taurus said:**
> Plug the drive into your machine and post the output of these commands from a terminal.

```
dmesg | tail 
sudo fdisk -l
```

This time I plugged in the Maxtor drive to the Ubuntu machine before booting up the computer. And when Ubuntu booted up, the external drive was mounted! I don't know why. But now I can copy and paste files onto the drive and it seems to be working perfectly normally, at least in Ubuntu. I'll gave to reboot into Vista and see if it works there or not. Because up till now it wasn't working in Vista even after having reformatted it as NTFS usinig gparted.

Here is the output of the two commands above requested:

```
:~$ dmesg | tail 
[  699.116466] sd 7:0:0:0: [sdc] Mode Sense: 23 00 00 00
[  699.116473] sd 7:0:0:0: [sdc] Assuming drive cache: write through
[  699.119329] sd 7:0:0:0: [sdc] 1970176 512-byte hardware sectors (1009 MB)
[  699.120080] sd 7:0:0:0: [sdc] Write Protect is off
[  699.120085] sd 7:0:0:0: [sdc] Mode Sense: 23 00 00 00
[  699.120092] sd 7:0:0:0: [sdc] Assuming drive cache: write through
[  699.120096]  sdc: sdc1
[  699.121058] sd 7:0:0:0: [sdc] Attached SCSI removable disk
[  699.121129] sd 7:0:0:0: Attached scsi generic sg4 type 0
[  746.976295] usb 6-3: USB disconnect, address 3
:~$ sudo fdisk -l
[sudo] password: 

Disk /dev/sda: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1fe519d7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19929   160079661    b  W95 FAT32

Disk /dev/sdb: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe0000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1           5       40131   de  Dell Utility
/dev/sdb2               6        1311    10485760    7  HPFS/NTFS
/dev/sdb3   *        1311       18178   135481344    7  HPFS/NTFS
/dev/sdb4           18179       19452    10233405    5  Extended
/dev/sdb5           18179       19392     9751423+  83  Linux
/dev/sdb6           19393       19452      481918+  82  Linux swap / Solaris
:~$ 


```

Does it look like there could still be something wrong with the drive? Would you recommend that I go ahead and write zeros to it? I'll try going into Vista again now and see if it works or not.

---

### Post by cdtech on 2008-11-29
> **swarup said:**
> I have a 150 GB external Maxtor HD, and the other day my colleague had it connected to a computer that was running Vista, and the external HD got disconnected before the computer was completely turned off. As a result, the HD is now acting dysfunctionally.
For future reference......

Any time you remove an NTFS unsafely just run "ntfsfix" through Linux on the device. This will reset the NTFS journal.
```
sudo ntfsfix /dev/sdb
```
**UPDATE::.**
Sorry nebu, just read your post. lol

---

### Post by swarup on 2008-11-29
To cdtech and nebu, et al:
I have already reformatted the drive as NTFS using gparted, as mentioned in my first post. Having done so, is there still a role for ntfsfix here? I very much appreciate this info you've given, for future knowledge and use-- but now that my drive is reformatted (it took all of 5 seconds in gparted i.e. it was the "quick" type of reformat), ntfsfix won't help, will it?

I have gone back into Vista, and it is still not recognized there. So the drive now seems to be functioning normally in Ubuntu (mounts fine) as well as in XP, but in Vista it is not getting recognized. And unfortunately, the Vista computer is where that drive is mainly to be used.

Further thoughts or suggestions? Thanks!!

---

### Post by cdtech on 2008-11-29
I've heard that formating to NTFS through "gparted" has some issues with Vista, so formating to NTFS using XP or Vista would let Vista see the drive then all OS's will see the drive as NTFS.

---

### Post by swarup on 2008-11-29
> **cdtech said:**
> I've heard that formating to NTFS through "gparted" has some issues with Vista, so formating to NTFS using XP or Vista would let Vista see the drive then all OS's will see the drive as NTFS.

I see. But Vista is not seeing the drive and so cannot be used to format it. And XP, although it sees the drive and can paste files into it and open those files, but XP's disk management utility sees the drive as "bad" and will not perform any format or other functions. 

So in view of this, would do you suggest should be my next step? Perhaps I should try the Maxtor utility "Maxblast", mentioned by Olivier2371. Perhaps it will work using the XP machine. Using that if I can write zeros to the drive, then perhaps the drive will start to work normally?

---

### Post by Olivier2371 on 2008-11-29
Yes use my solution. Beware that you will have to options, 

1 to Zero the drive completely
2 to zero the first and last sector.

The first option takes a while because initialises completely the drive.

You can use then maxblast again to create a new partion.

The second option doesn't take long but I don't know if it will resolve your problem.

---

### Post by swarup on 2008-11-30
> **Olivier2371 said:**
> Yes use my solution. Beware that you will have two options, 

1 to Zero the drive completely...

Thanks for the suggestion and info. :) I don't have access to the drive right now because it is with my colleague. In the next two days or so I should be able to do it. I'll write again here and let you know how it goes.

---

