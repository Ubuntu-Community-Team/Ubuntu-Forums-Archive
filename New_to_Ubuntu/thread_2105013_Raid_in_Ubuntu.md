---
title: "Raid in Ubuntu"
date: 2013-01-14
forum: New to Ubuntu
---

### Post by MikeYak on 2013-01-14
Hi ,I'm new to This forum and new to Ubuntu ,been mucking around with it for about a month.Have 12.04 (64 bit) loaded and useing it.I have some spare hard drives to experiment with ,and have tried to set up a raid array with 2 disks,and cant get it to work.I am not a professional I.T guy.I'd like to first set up a raid with stri ping and no back up,and go from there on my learning curve. I cant seem to find instructions from scratch on how to do this.I dicovered this 
 mdadm --create /dev/md0 --level=1 --raid-devices=2 /dev/sda1 /dev/sdb1
,altering the drive names accordingly from a third disk thats not to be included form the raid.Ive also tried different partitioning ,still not working.Raid 0 is what im looking for i think
Do I need the server version of Ubuntu for this to work,perhaps?
Im probably missing something obvious.Hope someone can help.Thanks

---

### Post by steeldriver on 2013-01-14
No you don't need the Server version - you just need the mdadm package to be installed (it isn't installed by default in the Desktop version iirc)

What error are you getting exactly?

FYI level=1 would be mirrored rather than striped I think

---

### Post by CharlesA on 2013-01-14
> **steeldriver said:**
> 
FYI level=1 would be mirrored rather than striped I think

Correct.

If you really want raid0, go for it, but if one drive goes out you lose the whole array.

---

### Post by MikeYak on 2013-01-15
Hi,thanks for the replies,I'll set the disks up again and post the error messages,Yes I've installed mdadm,and i understand the consequences of striping without back up ,but its just to see if I can get it to work(nothing important on these disks),then I can look at more complex ? options.Thanks

---

### Post by MikeYak on 2013-01-16
Hi ,back again,I'finally got to the point of setting up a raid 0 array .Started with this 
mdadm --create /dev/md0 --level=1 --raid-devices=2 /dev/sda1 /dev/sdb1  
then corrected it to this:
   sudo mdadm --create /dev/md0 --level-0 --raid-devices=2  /dev/sdb /dev/sdc 
which worked! Gave me an array of unpartioned disks.
I then partitioned them with gparted,which also worked ,except it wiped ubuntu 12.04 from the dev/sdb disk and dev/sdc is empty except for swap partition. dev/sda  is the disk Im using to give terminal commands to the other 2 disks,and is not included in the array.
   The array after setting it up was automatically renamed to /dev/md127  ?? for an unknown reason.
    If I try to reload ubuntu back onto the array it sees the disks as individual disks ,so I have to install it on one or the other ,but it also wants to repartition the disk.
 My question is how can i get ubuntu os back onto the array discs and/or copy the whole of dev/sda onto the array disks? Thanks Mike

---

### Post by steeldriver on 2013-01-17
> **MikeYak said:**
> The array after setting it up was automatically renamed to /dev/md127  ?? for an unknown reason.

Does your /etc/mdadm/mdadm.conf file reflect the newly created array? if not you may need to append the array info with

```

sudo mdadm --detail --scan | sudo tee -a /etc/mdadm/mdadm.conf

```

If it's currently got the 'wrong' name then you may need to stop and reassemble it with the right (md0) name first.

IIRC you then also need to run
```
sudo update-initramfs -u
```to import this info (including the array numbering) into the initial RAM image so that the system knows how to label the array at boot time.

> **MikeYak said:**
> 
    If I try to reload ubuntu back onto the array it sees the disks as  individual disks ,so I have to install it on one or the other ,but it  also wants to repartition the disk.
 My question is how can i get ubuntu os back onto the array discs and/or  copy the whole of dev/sda onto the array disks? Thanks Mike

If you try to install from the desktop iso, I don't think it will understand the RAID config (the Desktop iso doesn't include mdadm) - you would need to install mdadm again on the live system before going to 'Install Ubuntu'. Alternatively it may be possible to clone your existing installation from sdaX either using 'dd' or one of the other clone tools like clonezilla.

There are a couple of real RAID experts on the forum so they will be able to advise you

---

### Post by MikeYak on 2013-01-18
Thanks Steel Driver I'll try your suggestions and se how i go .Thanks

---

### Post by MikeYak on 2013-01-18
Thanks Steel Driver I'll try your suggestions and se how i go .Thanks

---

### Post by MikeYak on 2013-02-03
Back again.I've used the alternate Install of Ubuntu 12.04,and have been able to use the partition manager to create Md0 instead of mdadm,but once that is done I cannot get the rest of the ubuntu installation to finish.
   Does it make a difference that the 2 drives I'm using are different speeds? One is 5400 and the other 7200 rpm? This is for a Raid 0 configuration.Thanks Mike

---

### Post by ronparent on 2013-02-04
For a raid0 especially, it is recommended that both dives be identical!

---

