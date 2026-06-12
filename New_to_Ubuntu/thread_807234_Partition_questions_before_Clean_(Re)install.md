---
title: "Partition questions before Clean (Re)install"
date: 2008-05-25
forum: New to Ubuntu
---

### Post by Unstuck on 2008-05-25
I want to do a clean install over the original installation.  Hardy is located on /dev/sda1, and /home is on /dev/sda3.

I'm nervous about doing this so I want to double check that my partitions are done correctly.  I think that the partition options for sda1 are as follows:
Use As: ext3
Mount point: /

sda3:
Use As: ext3
Mount point: /home

I'm not sure if the mount point for sda1 is correct or if sda3 should even be touched...can't it be added as the location of /home via fstab after the install?

---

### Post by sayakb on 2008-05-25
/home will be automatically located and mounted. Your sda1 mountpoint is correct.

---

### Post by bwhite82 on 2008-05-25
That is correct. Be sure you have a swap partition as well.

---

### Post by Unstuck on 2008-05-25
Thanks, everyone!

---

