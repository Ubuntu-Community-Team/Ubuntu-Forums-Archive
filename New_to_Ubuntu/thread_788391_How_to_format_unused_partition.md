---
title: "How to format unused partition"
date: 2008-05-09
forum: New to Ubuntu
---

### Post by O-pos on 2008-05-09
Hi,

I just installed Ubuntu Gutsy. I have all the separate partitions for swap, root, home, as well as windows. I left the rest of the hard drive (100 GB) to use for my documents. In the installer it was mentioned as "unused", It did not get formatted and now I cannot use it anymore. Is there any chance to format this unused partition and use it to store all my music and other files?

Thanks.

---

### Post by macaholic on 2008-05-09
You can format partitions with gparted, sudo apt-get install gparted. Hope that helps.

---

### Post by shifty_powers on 2008-05-09
install gparted

```
sudo apt-get install gparted
```

just be careful what you're doing in there ;)

---

### Post by scragar on 2008-05-09
gparted(for ubuntu and Xubuntu) or qtparted(for Kubuntu) will both let you easily format the partition without any real problems(quick warning, gparted is a little slow to load if you've got a large HD or several USB's in)

```
sudo apt-get install gparted
```

---

### Post by O-pos on 2008-05-09
I installed gparted, but but it does not start stating that only root can use it. What should I do?

---

### Post by scragar on 2008-05-09
```
gksudo gparted
```

---

### Post by O-pos on 2008-05-09
ok. it says that more than four primary partitions is not possible and that's why this space is unallocated. What should I do?

---

### Post by scragar on 2008-05-09
use an extended partiton as a wrapper to let you put 2 orther partitions inside it

---

### Post by O-pos on 2008-05-09
That's a good idea. How can I fuse this with /home partition to create one extended partition and then subdivide it into home and my data?

---

### Post by O-pos on 2008-05-09
Any ideas how to create this extended partition with gparted?

---

### Post by plucky on 2008-05-10
> Any ideas how to create this extended partition with gparted? 




1) Delete the swap partition
2) Create the extended partition to encompass the unused space
3) Recreate the swap partition in the extended partition
4) Create any new partitions within the extended partition you need.
5) Boot ubuntu and it will probably give an fsck error status 8.Just CTRL D and it should continue the boot.
6) You need to change the UUID in /etc/fstab for the swap partition.
7) Mount the new swap partition



Good luck

---

### Post by scragar on 2008-05-10
Just extend the virtual partition around your swap partition to take up all of your free space, then create your partition you want to store files in inside it.

---

