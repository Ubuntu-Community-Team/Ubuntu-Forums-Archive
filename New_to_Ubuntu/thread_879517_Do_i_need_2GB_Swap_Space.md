---
title: "Do i need 2GB Swap Space ?"
date: 2008-08-04
forum: New to Ubuntu
---

### Post by chinnaraaju on 2008-08-04
Hi,

When I installed ubuntu ,I created a 2GB swap for good measure. However I want some more space for other partitions and am not ready for another hard disk, so I want to know if I can bring down the swap size to maybe 1GB or less,if so how to do that. 

i have 512 MB of RAM inside, So isnt it safe to limit my swap to 1GB? or What Swap size could be good for my system now ?

Regards,
Chinna.

---

### Post by muted1987 on 2008-08-04
hi also have 512 of ram and a 1 gig swap space and i havnt found any problems yet as to the "im not ready for anothe hard drive" what does that mean

---

### Post by Elfy on 2008-08-04
If you go for the 1.5xRAM then about 750MB should be sufficient for swap - you can boot your buntu livecd and do the partitioning work in there. You will need to turn off swap before you start though

```
sudo swapoff -a
```


Edit - > "im not ready for anothe hard drive" what does that meanat aguess the OP doesn't want to buy one

---

### Post by Rocket2DMn on 2008-08-04
1 GB of swap should be more than sufficient for a computer with 512 MB RAM.  You will need to do your resizing of the swap from the Ubuntu LiveCD or GParted LiveCD - [http://gparted-livecd.tuxfamily.org/](http://gparted-livecd.tuxfamily.org/)
If you use the Ubuntu LiveCD, you will probably need to unmount the swap partition first since it may automount it (all partitions that get fiddled with must be unmounted).
When you reboot into Ubuntu, you may need to update the UUID for any adjusted partitions, cross check
```
sudo blkid
cat /etc/fstab
```
If you need to update fstab:
```
gksudo gedit /etc/fstab
```

---

### Post by chinnaraaju on 2008-08-07
Hi,

is there any software or utility or tool available for resizing, which will be easier to do this?...

Regards,
Chinna.

---

### Post by Elfy on 2008-08-07
There is a partition editor on the livecd

---

### Post by kpkeerthi on 2008-08-07
Or use this one if you want the latest

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

Look in the documentation section at the site. Its quite extensive.

---

### Post by dileepm on 2008-08-07
You may use the partition editor called GParted available in CD as well as in [http://packages.ubuntu.com/](http://packages.ubuntu.com/) it works fine.However for security reasons it is made slower to check for all disk/partition errors...

---

