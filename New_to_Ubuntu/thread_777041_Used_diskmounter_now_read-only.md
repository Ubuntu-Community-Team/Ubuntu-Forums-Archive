---
title: "Used diskmounter now read-only"
date: 2008-05-01
forum: New to Ubuntu
---

### Post by ubunfan on 2008-05-01
Hi All

I have all my music on a slave drive so I used the diskmounter script to automatically mount the drive when Ubuntu 8.04 starts. 

The problem now is that the drive is now read-only. I'm new at this so I'm guessing I need to edit something in the fstab file. Here's the 2 additional entries that are in the fstab file since I ran the diskmounter script.

#Added by diskmounter utility
/dev/sda1 /media/sda1 ntfs ro,user,fmask=0133,dmask=0022,uid=1000,gid=1000 0 0
#Added by diskmounter utility
/dev/sdb1 /media/sdb1 ntfs ro,user,fmask=0133,dmask=0022,uid=1000,gid=1000 0 0  

Any help would be much appreciated.

---

### Post by ubunfan on 2008-05-01
All fixed thanks to "frogitts". I used the advice he gave in another thread and installed the NTFS Configuration Tool via the Add/Remove - many thanks.

---

