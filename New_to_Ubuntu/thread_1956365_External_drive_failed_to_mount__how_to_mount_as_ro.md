---
title: "External drive failed to mount : how to mount as root?"
date: 2012-04-10
forum: New to Ubuntu
---

### Post by ButchMel on 2012-04-10
I have one of these hasstles WD MyBook (plugged Firewire 400) on Ubuntu Server recently installed.  

Usially, even after a shutdown, this drive mount without problem. However this shutdown was over 24 hours and for some reason, the drive failed to mount, so I had to skip during boot process.

Now, although I can see in in Disk Utility (graphic interface), I cannot mount it and get an error message: ''Error mounting: mount exited with exit code 1: helper failed with:
mount: only root can mount /dev/sdd1 on /media/Backup_WD_MyBook''

So can I asume i could mount it as root and if so, how do I proceed? (either command line in terminal or in the graphic interface). Please be as detailed a spossible, I'm green to this....

Thanks,

---

### Post by papibe on 2012-04-10
Hi ButchMel.

I'm a little confused, about the disk being connected to a Server edition or a Desktop edition.

If I were on a server, I would do something like:
```
sudo mount /dev/sdd1 /media/Backup_WD_MyBook
```
But if on a DE, I just unplug the cable, count to 3, and plug it again, so it gets automounted.

Does that make sense?
Regards.

---

### Post by ButchMel on 2012-04-10
> **papibe said:**
> If I were on a server, I would do something like:
```
sudo mount /dev/sdd1 /media/Backup_WD_MyBook
```
 
Does that make sense?
Regards.
 
Absolutely ! Thanks for this one, Papibe. it worked (yes I am on a server edition: 10.04.4).
 
However, I tried the same thing with the other partition of this external drive, and got the following:
 
sudo mount /dev/sdd2 /media/NetAccess_WD_MyBook
fuse: failed to access mountpoint /media/NetAccess_WD_MyBook: No such file or directory
 
I checked everything in Disk Utility: it's really sdd2, and the name appears like this. 
 
Just to make 100% sure, here is the error I also get if I try it under Disk Management:
 
Error mounting: mount exited with exit code 1: helper failed with:
mount: only root can mount /dev/sdd2 on /media/NetAccess_WD_MyBook
 
What am I missing ?


(If this can help, here is the result to sudo fdisk -l :

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xeae9456b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1      121602   976759808    7  HPFS/NTFS

Disk /dev/sdb: 82.0 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000a2261

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1          32      248832   83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sdb2              32        9965    79792129    5  Extended
/dev/sdb5              32        9965    79792128   8e  Linux LVM

Disk /dev/sdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x790f3e19

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        9729    78148161    7  HPFS/NTFS

Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x8d399bc0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       63742   512000000    7  HPFS/NTFS
/dev/sdd2           63742      121601   464758784    7  HPFS/NTFS

---

### Post by ButchMel on 2012-04-13
No one can explain that one ? 

I'm still stucked with the problem.... (Just wonder if a simple reboot could fix that, but I don't want to loose what I solved)....

---

### Post by Bushflyr on 2012-04-13
```
sudo mount /dev/sdd2 /media/NetAccess_WD_MyBook
fuse: failed to access mountpoint /media/NetAccess_WD_MyBook: No such file or directory
```

I'm still super new, so take it FWIW, but does the directory */media/NetAccess_WD_MyBook* exist? I've gotten those messages when I forgot to 
```
sudo mkdir /media/NetAccess_WD_MyBook
```

It's case sensitive. Also, backup that POS Mybook ASAP. I had one fail on me. The drives were fine but something in the controller crashed and everything was lost. Even plugging the drives in to another machine individually and ripping them bit by bit couldn't save much.

---

### Post by ButchMel on 2012-04-13
> **Bushflyr said:**
> ```
sudo mount /dev/sdd2 /media/NetAccess_WD_MyBook
fuse: failed to access mountpoint /media/NetAccess_WD_MyBook: No such file or directory
```

I'm still super new, so take it FWIW, but does the directory */media/NetAccess_WD_MyBook* exist? I've gotten those messages when I forgot to 
```
sudo mkdir /media/NetAccess_WD_MyBook
```

It's case sensitive. Also, backup that POS Mybook ASAP. I had one fail on me. The drives were fine but something in the controller crashed and everything was lost. Even plugging the drives in to another machine individually and ripping them bit by bit couldn't save much.

Thanks for your reply. Just wondering: in my case, this has worked for over a week. Would you mean that Linux could sort of "forget" the path or directory? 

When I am in Disk Utility (graphic interface) i do see that partition. It's just that I can 't mount it (nor get in)...

Thanks

---

### Post by ButchMel on 2012-04-13
> **Bushflyr said:**
> ```
sudo mount /dev/sdd2 /media/NetAccess_WD_MyBook
fuse: failed to access mountpoint /media/NetAccess_WD_MyBook: No such file or directory
```

I'm still super new, so take it FWIW, but does the directory */media/NetAccess_WD_MyBook* exist? I've gotten those messages when I forgot to 
```
sudo mkdir /media/NetAccess_WD_MyBook
```


Wow ! I finally took a chance and tried your suggestion and it worked :-)  Many thanks ! I've been stucked with this for 3 days.  Still strange that it worked before. Like if shutting down for 24 hours had erased that path or what?  Anyway, many thanks !

---

### Post by Bushflyr on 2012-04-13
Cool, glad it worked. Sometimes weird stuff goes on. Dunno. 

*ETA*: You should probably mark this as solved.

---

