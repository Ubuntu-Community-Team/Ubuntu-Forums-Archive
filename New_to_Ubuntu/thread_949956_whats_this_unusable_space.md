---
title: "whats this unusable space ?"
date: 2008-10-16
forum: New to Ubuntu
---

### Post by equanimous1 on 2008-10-16
Hi 
I'm very new so please excuse my ignorance.
tryingg to install on 120 gb partiton an alredy partitioned HD , winXP on another partition and 20gb reserved to share (perhaps ) 

I managed to create the mount point  / and the swap space  then the rest of the space is marked as unusable and I'm not able to create /home ? 

what am i doing wrong 
!?

:(

---

### Post by Sarmacid on 2008-10-16
You can only have 4 primary partitions on a hard drive, so I would suggest opening up gparted, delete the swap partition and make it again specifying that it will be logical, not primary. Then you can make some more logical partitions.

---

