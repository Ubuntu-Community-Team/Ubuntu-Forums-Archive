---
title: "delete partitions"
date: 2013-03-15
forum: New to Ubuntu
---

### Post by RGGoldr on 2013-03-15
**I need to remove Ubuntu 12.10 so that I can install XP Pro.  I tryed using Gparted but it gave me the error message, "The partition could not be unmounted from the following mount points**. "/" Most likely other partitions are also mounted on these mount points.  You are advised to unmount them manually.  I have tryed using "Fdisk" at the command prompt, but the commands "p", and "d" would not work.  I have no idea what to do here.  Can anyone help.  Or do I need to follow another path.

---

### Post by oldfred on 2013-03-15
You cannot use gparted to delete or edit the partition you are working from. If on anther drive you should be able to unmount it and then edit it. 

You also have to unmount swap if using liveCD which is usually recommended, so you have no issues of mounted partitions.

       GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

---

### Post by deadflowr on 2013-03-15
If you have two hard drives unplug the one you don't want to install xp on, and load the xp installation disk and wipe and reformat it there.
Probably the safest and simplest method.

---

