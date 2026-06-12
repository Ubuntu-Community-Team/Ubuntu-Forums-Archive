---
title: "Remove ubuntu"
date: 2011-12-22
forum: New to Ubuntu
---

### Post by art_monu on 2011-12-22
HII..
I had installed ubuntu alongside windows using live cd(10.04) and not using wubi. I didn't specified partitions manually and let ubuntu install on its own. I tried upgrading it to 11.10 but a fatal error occurred and could not complete the up-gradation. After restarting, ubuntu was not working. I want to completely remove 10.04 and freshly install 11.10 but its not a wubi install and I don't know how to remove ubuntu as there is no separate partition for it too. 

Please help me.:(

---

### Post by Paqman on 2011-12-22
If you boot up into your LiveCD and run Gparted you should be able to see the partitions created the first time around. Make a note of which one is the EXT4 partition, this will be your main Ubuntu partition. When you run the 11.10 installer you can specify manual partitioning, and tell the system to format that partition as EXT4 again, and set the mount point as /. You don't need to re-format the swap partition.

---

### Post by art_monu on 2011-12-22
thanks..

---

