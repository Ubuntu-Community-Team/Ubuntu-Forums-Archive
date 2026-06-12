---
title: "[SOLVED] Trouble mounting NTFS hard disk"
date: 2008-10-13
forum: New to Ubuntu
---

### Post by destructogus on 2008-10-13
Hi all,
I know there are lots of how to's for mounting a hard disk, but nothing really seems to help me.

I was running an ubuntu 6.06, and decided to upgrade to 8.04.  I previously had two hard drives mounted, (one native linux w/ swap and all that) and an NTFS one (i think), and another one (unmounted) just sitting there.

I haven't physically opened up the computer or anything, and I know both hard drives were working a few days ago.

I installed ubuntu server 8.04, and I am using webmin to administer the computer.

When I came to remount the hard drive, this is what i got.

```
> fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xda23cb9c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9541    76638051   83  Linux
/dev/sda2            9542        9729     1510110    5  Extended
/dev/sda5            9542        9729     1510078+  82  Linux swap / Solaris

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x73ce658a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       24321   195358401    7  HPFS/NTFS

Disk /dev/sdc: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xad7ead7e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       14593   117218241    7  HPFS/NTFS

> mount -t ntfs-3g /dev/sdb1 /mnt/200gig 
NTFS signature is missing.
Failed to mount '/dev/sdb1': Invalid argument
The device '/dev/sdb1' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?
```

(Mounting via Wevmin results in the same error message)

Now, I know that this hard drive (/dev/sdb1) should work, because it working a few days ago, and I haven't changed any of the physical settings.  Also, I managed to mount /dev/sdc1 via webmin, incase that helps.


Suggestions?

Thanks,
Sam

---

### Post by jemate18 on 2008-10-13
just try

sudo mount -t ntfs /dev/sdb1 /mnt

---

### Post by Forbees on 2008-10-13
do you have windows booting on the NTFS?

if so, boot to windows and shut down proporly (start menu shutdown)

that astrisk makes me think of a fragmented drive, ubuntu will not touch a windows partition if it wasn't shut down properly

---

### Post by destructogus on 2008-10-14
hi,

Thanks jemate18 for your suggestion, I tried it, didn't work :(
```
> sudo mount -t ntfs /dev/sdb1 /mnt
NTFS signature is missing.
Failed to mount '/dev/sdb1': Invalid argument
The device '/dev/sdb1' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?

```

And, no, there's no windows on that hard drive. (or any of them actually), I left them as NTFS because it still had data on them (last time), which is why I don't want to reformat it.

---

### Post by jemate18 on 2008-10-14
is your ntfs drive still working? It might have been damaged though....

---

### Post by destructogus on 2008-10-14
Hmm... I put the hard drive in my win xp machine.  It detected the hard drive fine, mounted to (F:) drive.  But when I tried to view the files, it said that the hard drive wasn't formatted.

I think I have accidentally formatted or killed the filesystem on the HD when I was reinstalled ubuntu.  I've considered the data lost (just some torrents).

I'll reformat the hard drive (linux native) and then try and mount. 

Thanks for all your help. [Solved]

Sam

---

