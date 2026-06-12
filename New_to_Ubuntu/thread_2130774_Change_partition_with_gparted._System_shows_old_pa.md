---
title: "Change partition with gparted. System shows old partition-size"
date: 2013-03-30
forum: New to Ubuntu
---

### Post by Azyx on 2013-03-30
I have expand /-partion and thrinked /home/ on a extended partiton /sda3.

[ATTACH=CONFIG]240745[/ATTACH]
As you can see in the picture above. System-monitor and Gparted are Screenshoted at the same time.

How can that bee? How can I fix it?

It is on Ubuntu 10.04LTS

Edit. Before my change the /-partition was filled with around 18GB (as system-monitor show), so there should have being only the half /-partion, filled with files as it was extended to 37GB.

---

### Post by wildmanne39 on 2013-03-30
*Thread moved to **Absolute Beginners Section**.*

---

### Post by oldfred on 2013-03-30
Seems very strange.

Just to add a third choice what does this show?
df -h

And to see sector details:
 sudo fdisk -lu /dev/sda
sudo parted /dev/sda unit s print

---

### Post by sudodus on 2013-03-30
Have you backed up your personal files to another drive? Do it if you haven't and it is possible!

Then I suggest that you exit gparted and reboot the computer. What will you see after reboot?

---

### Post by The Cog on 2013-03-30
I've had issues with programs not knowing that the partition size has changed too. I don't remember which ones were the problem, but I do remember that a reboot gets it sorted out.

---

### Post by Azyx on 2013-03-30
> **oldfred said:**
> Seems very strange.

Just to add a third choice what does this show?
df -h

And to see sector details:
 sudo fdisk -lu /dev/sda
sudo parted /dev/sda unit s print

Hey. My post was moved by a admin, so It sees that I don't get any notifaction....

```
Azyx@Intel:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5              20G   18G  966M  95% /
none                  2,0G  440K  2,0G   1% /dev
none                  2,0G   14M  2,0G   1% /dev/shm
none                  2,0G  440K  2,0G   1% /var/run
none                  2,0G     0  2,0G   0% /var/lock
none                  2,0G     0  2,0G   0% /lib/init/rw
/dev/sda6             107G   93G  9,0G  92% /home
Azyx@Intel:~$ sudo fdisk -lu /dev/sda

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000866c3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63     4192964     2096451   82  Linux swap / Solaris
/dev/sda3         4193026   312576704   154191839+   5  Extended
/dev/sda5         4193028    83560447    39683710   83  Linux
/dev/sda6        85161984   312575999   113707008   83  Linux
Azyx@Intel:~$ sudo parted /dev/sda unit s print
Model: ATA WDC WD1600AAJS-0 (scsi)
Disk /dev/sda: 312581808s
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start      End         Size        Type      File system     Flags
 1      63s        4192964s    4192902s    primary   linux-swap(v1)
 3      4193026s   312576704s  308383679s  extended
 5      4193028s   83560447s   79367420s   logical   ext4
 6      85161984s  312575999s  227414016s  logical   ext4

Azyx@Intel:~$ 


```

I haveeeeeeeeealso allready made a couple of reboots.

Cheers. To morrow I make backups. Seems that Unison dont copy hidden files... I have ssh on the backup machine, so it shoud be able to copy all files and maybe conserve the meta data on the files?


cheers

---

### Post by carl4926 on 2013-03-30
Did you try making the changes from the running system or from a Live session?

---

### Post by Azyx on 2013-03-31
It's not possible to umount filesystem used by system /root and /home.  I use a 12.04LTS 64-bit live session from SD-card. Could that be a problem to use 12.04 and 64bit on a 10.04LTS 32-bit?

Need to make a bigger / cos it full, but I will soon upgrade to 12.04LTS because 10.04LTS soon get to old. I have a graphical problem with the 12.04 live session (sceen showed duoble in the edges.

---

### Post by oldfred on 2013-03-31
I do not think so. If anything using gparted from a 12.04 version has a lot of improvements over the 10.04 version.

---

### Post by Impavidus on 2013-03-31
Not only is your / full, your /home is full too. With both partitions over 90% used your performance will decrease and there's nothing you can do about that by just repartitioning your drive. You either need a major cleanup – which for most people doesn't work for exactly the same reason as for why they filled up their hard drive in the first place – or a bigger drive.

---

### Post by Azyx on 2013-03-31
It was totaly wrong. I expand /-partition from 20GB to 37GB just for that reason that / was full and suddenly the partion shows near 35GB. I I booted up another time with 12.04LTS 32-bit and made a litte change in Gparted and now it work again:)  Now will I see if my computer are able to run 12.04. I get a bad sceen as I have shown in another post :(

---

