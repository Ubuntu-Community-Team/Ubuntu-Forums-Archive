---
title: "Ubuntu fault"
date: 2013-02-18
forum: New to Ubuntu
---

### Post by GEOFFSKI on 2013-02-18
We had ubuntu installed a few years ago by a friend of ours and it has worked for years without any problems .yesterday while updates were being installed my daughter turned the power off by mistake. Now all that comes onto the screen is "you are in low graphics mode " the mouse does not work and it doesnt start up. Any advice please

---

### Post by sudodus on 2013-02-18
Welcome to the Ubuntu Forums :-)

Ask your friend to come with her/his Ubuntu install disk and help you repair the system. It might be enough to repair the file system of these partitions

/ (root) and if they exist /home and /boot 

Probably you have only the root partition.

Boot from the Ubuntu install disk and check which partition is mounted as /

Then run ```
sudo e2fsck -f /dev/sdxy
``` where x is the drive letter and y is the partition number.

---

### Post by Frogs Hair on 2013-02-18
> We had ubuntu installed a few years ago by a friend of ours and it has worked for years without any problems

Make sure you still have a supported version.If you are running 10.04 you will have support until April. [https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

---

