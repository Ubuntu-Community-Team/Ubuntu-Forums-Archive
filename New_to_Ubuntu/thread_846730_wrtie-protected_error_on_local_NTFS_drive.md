---
title: "wrtie-protected error on local NTFS drive"
date: 2008-07-01
forum: New to Ubuntu
---

### Post by deathvalleyjoker on 2008-07-01
I have a 250 Gb hard drive that is split into 3 partitions:

80Gb-Win XP
30Gb-Ubuntu 8.04
120Gb-NTFS "file storage"

i made the 3rd partition so that the two O/S's could have a common file area such as pitures and such. 

i put all old "my documents" from b4 the formate of dual booting, and put them in common storage drive.

i can read from it fine, but i get the following error message when i try to write to it. 

/media/sda5/My Pictures/post secret-college humor/chief2.jpg could not be saved, because the disk, folder, or file is write-protected.

Write-enable the disk and try again, or try saving in a different location. 

i am sure it has to do with permissions in windows, and i will ahve to fix it from there, but not sure exactly how the write protection should look for what i am trying to do.

i could not find anything helpful in the forms when i tried my searches.

thanks, mike c.

---

### Post by drs305 on 2008-07-01
One of the easiest things is to install ntfs-config. It will allow you to write to NTFS partitions and set up fstab accordingly.

To install:
```
sudo aptitude install ntfs-config
```

To run:
System Tools, NTFS Configuration Tool

---

### Post by deathvalleyjoker on 2008-07-01
perfect!

Thank You.

---

