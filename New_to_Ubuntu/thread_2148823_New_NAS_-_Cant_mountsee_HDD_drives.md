---
title: "New NAS - Cant mount/see HDD drives"
date: 2013-05-26
forum: New to Ubuntu
---

### Post by GeordieJedi on 2013-05-26
Hi all.

OK, I've finally taken the plunge and gotten a fantastic nice new shiny NAS
(A Synolgy DS413J)

However I'm struggling to get my NAS HDDs mounted and visable on my PC/network.

I've ran through the setup (using Synolgy Disk Station Manager = DSM).
I can connect to the NAS via a web broswer fine.

My main question is this -

1. How do I now get my NAS and it's HDD's to appear/mount/be usable on my network
so that either PC can connect to it and share/swap data and files ?


Do I need to create some mount points in the FSTAB ?
I gave it a try and got the following error messages

This is what I have in my FSTAB file currently
```
Hoth:/volume1/photo /mnt/photo_share/photo nfs nouser,atime,auto,rw,dev,exec,suid 0 0
```


I have also installed the package "nfs-common".
Do I also need to install "nfs-kernel-server" ? 




Useful info

Ubuntu 12.04
DE = KDE


Virgin media cable modem/router (downstairs)
Cat cable run upstairs to switch (upstairs in office)
PCs and NAS connected to switch (upstairs in office)


Synology DS413J NAS =
2x 3TB HDD's in Synolgys hybrid RAID array (Kinda RAID 1) making a total of
2.68 TB usable space


Any help or advice would be grateful appreciated !
Thanks.

---

### Post by jpaulb on 2013-06-06
There  are a couple of ways that have worked for me with a D-Link DSN-321, The entry in fstab can be either

192.168.0.14:/Volume_1        /mnt          cifs  guest,_netdev,noperm  0  0
or
192.168.0.14:/mnt/HD_a2         /mnt        nfs    defaults 0 0

depending on whether you choose to use nfs or cifs . My NAS is located at 192.168.0.14.

IF  you get it running I would like to know how fast it is, The D-Link max  out at 3.2 MB/s when hooked to a giga bit network, which is way slower  than I can download from the internet.

---

### Post by GeordieJedi on 2013-10-20
bump

---

