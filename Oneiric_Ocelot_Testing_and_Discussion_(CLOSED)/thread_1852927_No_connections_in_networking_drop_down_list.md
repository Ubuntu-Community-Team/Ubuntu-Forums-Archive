---
title: "No connections in networking drop down list"
date: 2011-10-01
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by kanishkdudeja on 2011-10-01
earlier in ubuntu 11.04..there used to be connections listed under the applet displayed on the top right..but in 11.10 beta 2..im not able to see any connnections..

is there any new away to connect to a connection or is it just a bug?

---

### Post by MacUntu on 2011-10-01
> or is it just a bug?

This. Should already be fixed if you update from the main severs: [https://bugs.launchpad.net/dbusmenu/+bug/862989](https://bugs.launchpad.net/dbusmenu/+bug/862989)

---

### Post by kanishkdudeja on 2011-10-01
Well..

Im not able to connect using my data card in 11.10..

how do i update? :(

---

### Post by MacUntu on 2011-10-01
Boot a live CD, do whatever you need to do to connect to the internet. Now chroot into your old system:

```
sudo mount /dev/sda1 /mnt
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo cp /etc/resolv.conf /mnt/etc/resolv.conf
sudo chroot /mnt
apt-get update
apt-get upgrade
exit
```

Where you must change /dev/sda1 to whatever your Ubuntu partition is called (e.g., use 'sudo fdisk -l'). Next boot it should work fine again.

---

### Post by kanishkdudeja on 2011-10-01
does the live cd has to be same version that was installed? or it can be of some previous version too?

---

### Post by MacUntu on 2011-10-01
It doesn't matter which version the live CD is (as long as you can get internet with it, of course).

---

