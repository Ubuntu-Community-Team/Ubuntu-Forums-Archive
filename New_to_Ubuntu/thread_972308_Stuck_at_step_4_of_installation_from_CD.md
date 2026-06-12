---
title: "Stuck at step 4 of installation from CD"
date: 2008-11-05
forum: New to Ubuntu
---

### Post by plata46 on 2008-11-05
I tried to install ubuntu with cd. How do i get past step 4 prepare partitions. tks. plata46

---

### Post by WRDN on 2008-11-05
It depends what type of installation you want.
Have you got Windows installed, and do you want to setup a dual boot environment, or will Ubuntu use the entire drive.

If the latter is true, then you can just select "Use entire drive" (or words to that affect) and continue. Alternatively, create partitions to install ubuntu on (I recommend doing this in GParted that can be found in System > Administration). You can resize existing partitions here, and create new ones. I would recommend creating 3 partitions:

1 ext3 partition for root (/)
1 ext3 partition for /home 
and 1 swap partition

Once you have created these, choose Manual during the installer, select the root partition you created, click Edit Partition and give it the mount point "/". Do the same for the /home partition, and give it the mount point "/home".

---

### Post by mapes12 on 2008-11-06
I agree with the last post. That way you keep /home separate which makes any future upgrades very easy in terms of preserving files, personal settings, bookmarks and the like. 

However, I would burn a GParted Live CD and boot from that. This is because on some configurations trying to work on your HDD when the OS is ruuning from it can cause problems. A Live CD iso can be downloaded from this site: [http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

In planning your HDD partitioning you may like to have a look at this excellent guide: [http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning).

:lol:

---

