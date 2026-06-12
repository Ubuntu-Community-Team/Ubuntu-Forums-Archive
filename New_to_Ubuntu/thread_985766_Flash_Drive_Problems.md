---
title: "Flash Drive Problems"
date: 2008-11-17
forum: New to Ubuntu
---

### Post by ellika on 2008-11-17
Hi, I am new to ubuntu, and my knowledge is rather limited.  

I can't get it to let me open my flash drives or cds where I stored all of my documents and stuff before my computer crashed. It either says that I "am not privileged to mount this volume" (flashdrives) or it doesn't do anything at all (cds). 

I am clueless as to how to go about fixing this and I really need my documents back. I've looked around the forums and everyone seems to be on a much higher level computer knowledge wise than me and I'm hoping that it's a fairly simple problem that someone could help me correct. So any help, in noob friendly terms if at all possible, would be amazing. Thanks.

---

### Post by zzHanks on 2008-11-18
Are you the administrator of the system?
Go to System > Administration > Users and Groups and check your preferences and User privileges.

Hope this helps.

---

### Post by ellika on 2008-11-18
I went in there and it says that I am the administrator and I clicked all of the other user privileges too, but I still get the "cannot mount volume, you are not privileged to mount this volume" screen.

---

### Post by shifty_powers on 2008-11-18
how are you trying to mount it?

just by plugging it in or through the command line?

---

### Post by ellika on 2008-11-18
plugging it in, what would I type into the command line?

---

### Post by shifty_powers on 2008-11-18
does it show up on the desktop as an icon but it does not let you open it?

---

### Post by shifty_powers on 2008-11-18
```
sudo mount -t /dev/sdb1 /media/disk -o force
```

is an example, but it depends on your system...

---

### Post by ellika on 2008-11-18
No, I just plug it in and the error screen pops up.

---

### Post by shifty_powers on 2008-11-18
is it formatted as ntfs?

and has been used on a windows partition?

if so, try

```
sudo mount -t ntfs-3g /dev/sdb1 /media/disk -o force
```

---

### Post by ellika on 2008-11-18
when I type in that line you sent it says to put in my password, but it won't let me type anything.

---

### Post by Keen101 on 2008-11-18
> **ellika said:**
> when I type in that line you sent it says to put in my password, but it won't let me type anything.

Linux passwords are never displayed (for security reasons). just put in your password ans press [enter]. It should work. (assuming the command is correct that is)

---

### Post by ellika on 2008-11-18
and I have no idea if it is formatted as ntfs or not.

---

### Post by ellika on 2008-11-18
when i do that it says:

ntfs-3g: Failed to access volume '/dev/sdbl': No such file or directory
Please type '/sbin/mount.ntfs-3g --help' for more information.

and when i type in that line it says:

bash: /sbin/mount.ntfs-3g --help: No such file or directory

---

### Post by ellika on 2008-11-18
any suggestions?

---

### Post by Keen101 on 2008-11-18
can you do

```
sudo fdisk -l
```

---

### Post by ellika on 2008-11-18
it says:

Cannot open /dev/sda
Cannot open /dev/sdf

---

### Post by ellika on 2008-11-18
Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18697   150183621   83  Linux
/dev/sda2           18698       19452     6064537+   5  Extended
/dev/sda5           18698       19452     6064506   82  Linux swap / Solaris

Disk /dev/sdf: 4007 MB, 4007657472 bytes
16 heads, 32 sectors/track, 15288 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1              16       15288     3909696    c  W95 FAT32 (LBA)

---

### Post by ellika on 2008-11-18
okay I got the sudo mount -t /dev/sdb1 /media/disk -o force to work,

It says to type in `mount [-t fstype] something somewhere'. but then it says that only root can do that

what do I do now?

---

### Post by Keen101 on 2008-11-18
I'm not exacly sure, but it looks like your flash drive is mounted as /dev/sdf1 instead of /dev/sdb1, and it is FAT32, so that whole ntfs mounting stuff is not needed. As far as i can tell, your drive should work, but i'm not very knowledgeable when it comes to mounting drives. I could be wrong, and /dev/sdf1 could be a windowsxp partition if this is a dual boot system.

> /dev/sdf1 16 15288 3909696 c W95 FAT32 (LBA)

---

### Post by ellika on 2008-11-18
it isn't a dual boot system. i only have ubuntu right now because xp won't instal correctly. thanks for trying.

---

