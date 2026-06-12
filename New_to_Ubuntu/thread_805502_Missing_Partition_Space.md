---
title: "Missing Partition Space"
date: 2008-05-24
forum: New to Ubuntu
---

### Post by klausner on 2008-05-24
I moved the content of my hard disk to a larger drive using Clonezilla, though I manually partitioned the new drive first. After a few minor missteps, I got things up and running, but the two partitions I enlarged are missing most of their space! Even weirder, df and gparted produce different results.

df shows:
> 
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda7              6190664   2824924   3051272  49% /
varrun                  513120       108    513012   1% /var/run
varlock                 513120         0    513120   0% /var/lock
udev                    513120        72    513048   1% /dev
devshm                  513120        12    513108   1% /dev/shm
lrm                     513120     38176    474944   8% /lib/modules/2.6.24-16-generic/volatile
/dev/sda10            21797536    775440  21022096   4% /NTFS
/dev/sda1             32764532  24151284   8613248  74% /Windoze
/dev/sda6              1035628     70440    912580   8% /boot
/dev/sda8             10365264   8973908    864828  92% /home
/dev/sda9             10365264   9367092    471644  96% /usr/local
gvfs-fuse-daemon       6190664   2824924   3051272  49% /home/klausner/.gvfs
/dev/scd0                95732     95732         0 100% /media/cdrom0


while gparted shows:

[IMG]http://farm4.static.flickr.com/3141/2517266253_90fe7031fc_d.jpg[/IMG]

This is using Hardy, 8.04.

Also, why is my home directory (/home/klausner) mounting with gvfs-fuse-daemon? I didn't overtly do anything to cause this.

How do I get to use the missing space?
:-(

---

### Post by warbread on 2008-05-24
The .gvfs daemon thing is normal.  That's for network mountings.  

The problem I see is with sda8 and sda9.  Is that what you're talking about?  How big is your hard drive?

---

### Post by klausner on 2008-05-24
> **warbread said:**
> The .gvfs daemon thing is normal.  That's for network mountings.  

The problem I see is with sda8 and sda9.  Is that what you're talking about?  How big is your hard drive?

Yes, 8 and 9 are the problem. The drive is 160GB.

Why is my home directory being network mounted? I'm not currently using any network file services.

---

### Post by klausner on 2008-05-24
As a cross check, I booted the Ubuntu Live CD to see what the partitions looked like. df still showed both sda8 and sda9 truncated at 9.9GB each, when they should be 40GB and 45GB respectively. Curiously, Nautilus reports the correct sizes for the volumes.

Why is Hardy truncating these partitions, and how do I get the missing space back?

---

