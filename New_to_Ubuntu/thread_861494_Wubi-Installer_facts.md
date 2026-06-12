---
title: "Wubi-Installer facts"
date: 2008-07-16
forum: New to Ubuntu
---

### Post by texas.chef94 on 2008-07-16
I presently am using ubuntu 8.04 and the vehicle that accomplished that install was the wubi installer.
I could not be happier as it obviously is an innovative exciting option to arrive at Linux for a new user.
However at dual boot when I am given the choice between windows and Ubuntu, and choose Ubuntu I get a very quick message relative to it being an unrecognized partition table. It goes on to suggest that it can be rebuilt using fdisk.
I see no reason why it will not continue to work well as it has been working. I am merely curious because
1. documentation states it was loaded within windows and I think within a single folder.
2. Windows seems to not recognize the partition as there is none.
Would someone who knows what is going on with this HD configuration please advise.
Thanks
Allen

---

### Post by sdowney717 on 2008-07-16
wubi installs as a file on the NTFS partition.
So, is there another unknown partition? 
install gparted using synaptic and run it and see what it shows you.

---

### Post by smo0th on 2008-07-17
> **texas.chef94 said:**
> I presently am using ubuntu 8.04 and the vehicle that accomplished that install was the wubi installer.
I could not be happier as it obviously is an innovative exciting option to arrive at Linux for a new user.
However at dual boot when I am given the choice between windows and Ubuntu, and choose Ubuntu I get a very quick message relative to it being an unrecognized partition table. It goes on to suggest that it can be rebuilt using fdisk.
I see no reason why it will not continue to work well as it has been working. I am merely curious because
1. documentation states it was loaded within windows and I think within a single folder.
2. Windows seems to not recognize the partition as there is none.
Would someone who knows what is going on with this HD configuration please advise.
Thanks
Allen

this sounds like something related to an unclean shutdown, if you see an error 81 then it definitely is an unclean shutdown, anyway, try booting into wind0ze and type ```
chkdsk /f d:
``` assuming drive d is where you have your wubi installation. Reboot and you should be able to use ubuntu again :)

---

### Post by texas.chef94 on 2008-07-18
Thank you so much problem solved

---

### Post by smo0th on 2008-07-18
my pleasure ;)

---

