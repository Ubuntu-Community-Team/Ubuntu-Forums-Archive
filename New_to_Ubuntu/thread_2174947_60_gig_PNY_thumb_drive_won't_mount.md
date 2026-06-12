---
title: "60 gig PNY thumb drive won't mount"
date: 2013-09-16
forum: New to Ubuntu
---

### Post by craigshreve66 on 2013-09-16
Hello my name is Craig and I am really new to Unbuntu. I am having issues getting a PNY 60 gig thumb drive to mount on my system. Below is the error I am getting.

Error mounting /dev/sdb1 at /media/craig/PENDRIVE: Command-line `mount -t "exfat" -o "uhelper=udisks2,nodev,nosuid" "/dev/sdb1" "/media/craig/PENDRIVE"' exited with non-zero exit status 32: mount: unknown filesystem type 'exfat'

When I start my VMware Windows 7 there is no issue. 

Any ideas?

Thank you

---

### Post by oldfred on 2013-09-16
Is it formatted exFat? That is Windows proprietary.

I did see where they were finally developing reversed Engineered drivers, but it will be quite awhile before I would use them.

---

### Post by fireflower on 2013-09-17
> **oldfred said:**
> Is it formatted exFat? That is Windows proprietary. This. Had the same problem myself once. Windows has no problems formatting thumb drives in Fat32 and Ubuntu has no problems reading Fat32-formatted thumb drives.

---

### Post by kurt18947 on 2013-09-17
> **oldfred said:**
> Is it formatted exFat? That is Windows proprietary.

I did see where they were finally developing reversed Engineered drivers, but it will be quite awhile before I would use them.

I experimented with this when it was still a ppa. Both packages are now available in the repositories.  Installing from the ppa seemed to work okay.  I formatted a flash drive to exfat in Windows then plugged it into a *buntu installation.  It seemed to read & write simple files fine, I did not try formatting in Ubuntu. The two packages that show up in Synaptic are exfat-utils & exfat-fuse.  I haven't installed from repository but I expect they'd work as well. 

 I've read that Microsoft lawyered the crap out of the exfat file system so I don't know if there are any legal issues with those in the U.S.  I guess whether or not to use them would depend on the value of the data stored and availability of other backups in the event that the exfat flash drive became unreadable.

---

### Post by CeejRab on 2013-09-17
Hello Craig! Welcome to the ubuntu forums!

I believe the others are correct, it sounds like a filesystem format problem.

If you dont have anything important on this USB stick, i would recommend opening disk utility and choosing the usb stick from the list on the left. Here choose to format the drive and select "Master boot record". When complete, choose "format volume" at the bottom right, and choose FAT from the drop down list of filesystem types.

After that, click "Mount" and it should work fine between both OS's. 

All the best,

---

### Post by squakie on 2013-09-17
Excuse a dumb comment - but isn't going to FAT going to restrict the OP to less than the full size of the usb stick?  I thought the same limits on addressing still applied.

---

### Post by CeejRab on 2013-09-17
Not a dumb comment! Im not sure exactly as a matter of fact, but ive done it myself and the only limit a fat or fat32 ssd hd is that it cant handle a single file size larger than 4GB. If thats a problem, there are other filesystem formats to choose from just check into whatever one youd like to use and make sure its compatible with what you need :)

---

### Post by craigshreve66 on 2013-09-17
Thank you everyone this is a big help.

---

### Post by CeejRab on 2013-09-18
No problem Craig, our pleasures. If you've found what you need, please mark the thread as solved using thread tools at the top right of this thread. :) 

all the best,

---

### Post by fireflower on 2013-09-18
> **squakie said:**
> isn't FAT going to restrict the OP to less than the full size of the usb stick? Short version: No, the maximum file size and the total storage space of the stick are two completely different things.

Long version: As one user said, the file size limit is 4 GB. You will rarely if ever deal with files that size, and certainly not in an Ubuntu boot stick. The only time it ever happened to me was when copying over a blueray rip, and even then, the file was only a few megs over the limit. Maybe some hard-core graphic artists would deal with files that big. Still, it's an interesting question, I don't want you to think it's dumb. It's extremely important to point out the difference between max file size and total storage space. That there was such a thing as max file size is probably news to someone; it was to me, once upon a time.

---

### Post by oldfred on 2013-09-18
On Windows 2000 it is 32GB for FAT32.

 NTFS and Fat info:
FAT 4GB file max & no journaling 
[http://technet.microsoft.com/en-us/library/cc938932.aspx](http://technet.microsoft.com/en-us/library/cc938932.aspx)
[http://technet.microsoft.com/en-us/library/cc940351.aspx](http://technet.microsoft.com/en-us/library/cc940351.aspx)
[http://www.ntfs.com/ntfs_vs_fat.htm](http://www.ntfs.com/ntfs_vs_fat.htm)
[http://en.wikipedia.org/wiki/ExFAT](http://en.wikipedia.org/wiki/ExFAT)

---

### Post by squakie on 2013-09-18
> **oldfred said:**
> On Windows 2000 it is 32GB for FAT32.

 NTFS and Fat info:
FAT 4GB file max & no journaling 
[http://technet.microsoft.com/en-us/library/cc938932.aspx](http://technet.microsoft.com/en-us/library/cc938932.aspx)
[http://technet.microsoft.com/en-us/library/cc940351.aspx](http://technet.microsoft.com/en-us/library/cc940351.aspx)
[http://www.ntfs.com/ntfs_vs_fat.htm](http://www.ntfs.com/ntfs_vs_fat.htm)
[http://en.wikipedia.org/wiki/ExFAT](http://en.wikipedia.org/wiki/ExFAT)

Thanks, Oldfred.  I was sure I remembered something about the actual size of the file allocation table in FAT versus FAT32 versus NTFS that had something to do with the total size of the storage medium, but perhaps with a large enough cluster size it would handle it, but the large cluster size would kind of defeat the purpose.

Or it may be that I just don't remember enough now to be of any use. ;)

---

### Post by oldfred on 2013-09-18
I am there too.
The only reason I remember anything is good searchable notes. :)

---

### Post by craigshreve66 on 2013-09-20
Thank you everyone for your posts, I just went and got a smaller thumb drive and it works fine. Darn that Windows thing!! Oh well I got around it.

---

### Post by kurt18947 on 2013-09-23
If you still want to use that 64 GB. thumb drive with Ubuntu/Linux, nothing says it has to stay exfat.  I'm using a smaller thumb drive plugged into a router functioning as an FTP server.  The thumb drive came formatted as FAT32, I fired up Gparted,  reformatted to ext4 and it works fine.

---

