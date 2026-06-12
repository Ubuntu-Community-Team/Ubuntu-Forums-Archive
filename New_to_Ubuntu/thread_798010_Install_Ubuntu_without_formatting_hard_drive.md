---
title: "Install Ubuntu without formatting hard drive"
date: 2008-05-17
forum: New to Ubuntu
---

### Post by dropscience on 2008-05-17
Hi, i was just wondering if there is any way i can reinstall Ubuntu from a cd without having to remove things from my hard drive. I was using 7.10 but when i updated to 8.04 i kinda messed up the OS. I cant start up Ubuntu at all and i would like to keep certain files on my hard drive. Can someone help me please?

---

### Post by Bodsda on 2008-05-17
boot into live cd and start the installer. When you get to the partition stage, choose manual, mount all the partitions there to there correct places by clicking on them and selecting properties then select their mount point from the drop down list, 

IMPORTANT

When you mount the /home partition make sure the 'format' tick box is UNTICKED. make sure all the others are ticked then do the rest of the install.

Hope this helps

---

### Post by shadow-of-sin on 2008-05-17
It depends on how your hard drive was formatted. Did you have all your data on a separate partition? If so, you can reinstall ubuntu and keep your data. However if you didn't have a separate partition, you'll have to boot into a livecd, recover your files onto some backup medium (external hard drive etc.) and then reformat your hard drive and reinstall ubuntu.

---

### Post by volkswagner on 2008-05-17
You can also boot the live cd and resize your partition.  Create/format a new partition, and transfer contents of home and other important data.

---

