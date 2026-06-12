---
title: "Hard drive space incorrect..."
date: 2008-04-25
forum: New to Ubuntu
---

### Post by isaacj87 on 2008-04-25
Hey all,

Just did a fresh install of Hardy...

I was looking at the Disk Usage Analyzer and it's telling me I have 139 GB of hard drive space. That seems odd to me since I have an 80 GB HDD. It's also telling me that I'm using 33 GB of that supposed 139 GB...

Is this a known bug? and if so, is there a fix available? 

Thanks in advance everyone :)

---

### Post by SOULRiDER on 2008-04-25
Whata re you using to view hard drive space?
Paste the output of
```
sudo fdisk -l
```
and
```
df -h
```
Lets see what that says.

---

### Post by isaacj87 on 2008-04-25
> **SOULRiDER said:**
> Whata re you using to view hard drive space?
Paste the output of
```
sudo fdisk -l
```
and
```
df -h
```
Lets see what that says.

Hey! Thanks for the quick reply...here's the output of fdisk:

> 
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000cd574

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9327    74919096   83  Linux
/dev/sda2            9328        9729     3229065    5  Extended
/dev/sda5            9328        9729     3229033+  82  Linux swap / Solaris


and "df -h"

> Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              71G   13G   55G  20% /
varrun                628M  104K  628M   1% /var/run
varlock               628M     0  628M   0% /var/lock
udev                  628M   56K  628M   1% /dev
devshm                628M   12K  628M   1% /dev/shm
lrm                   628M   38M  591M   6% /lib/modules/2.6.24-16-generic/volatile
gvfs-fuse-daemon       71G   13G   55G  20% /home/isaac/.gvfs
/dev/scd0             7.5G  7.5G     0 100% /media/cdrom0


---

### Post by SOULRiDER on 2008-04-25
> /dev/sda1 71G 13G 55G 20% /

Apparently youre using 13GB out of 71GB. What were you using to view disk space before?

---

### Post by isaacj87 on 2008-04-25
I was using the Disk Usage Analyzer found in Applications->Accessories...

I've been trying to figure out with Nautilus is performing slowly sometimes...For example, I have a folder that contains about 200 PNG and JPG files (wallpapers) and it takes forever to open up that folder. It has something to do with the new GFVS system or whatever right?

---

### Post by isaacj87 on 2008-04-25
> **SOULRiDER said:**
> Apparently youre using 13GB out of 71GB. What were you using to view disk space before?

Hmm..Well 13GB seems about right. Thanks for the help :)

If you have any solution for my slow Nautilus trouble, I wouldn't mind hearing it ;)

But once again, Thanks :)

---

