---
title: "Hardy Heron installation program"
date: 2008-05-15
forum: New to Ubuntu
---

### Post by js_anoop on 2008-05-15
I decided to install Hardy Heron on my 40 GB Hard Disk. This is the distribution of partitions.

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1354    10875973+   c  W95 FAT32 (LBA)
/dev/sda2            1355        4870    28242270    f  W95 Ext'd (LBA)
/dev/sda3            2439        2544      851413+  82  Linux swap / Solaris
/dev/sda5            1355        2544     9558643+   b  W95 FAT32
/dev/sda6            2545        3712     9381928+   b  W95 FAT32
/dev/sda7            3713        4870     9301603+   b  W95 FAT32

I have Windows XP installed on sda1. I want to install Hardy Heron on sda2 ( Will format to ext3 ) and thus dual boot.

I used the Live CD and when I reached the partition part, I selected 'Manual' partitioning. But instead of showing each partitions, it shows my whole disk /dev/sda. I have been using ubuntu from it 5.10 release. This is first time I am facing this problem. Please help.

---

### Post by Xiong Chiamiov on 2008-05-15
Do you mean that it shows your entire disk as one partition?  It should be showing all of sda, but it should be split up by partition.

---

### Post by MaindotC on 2008-05-15
If you click the /dev/sda partition it should expand and show the other partitions.  There is also an option to Edit Partition Table which should show all partitions on sda.

---

### Post by js_anoop on 2008-05-15
> Do you mean that it shows your entire disk as one partition? It should be showing all of sda, but it should be split up by partition.

Even gparted doesn't show my partitions. It shows my hard disk as unallocated 40 GB partition. But I can access all my partitions in Ubuntu Live CD itself.

---

### Post by MaindotC on 2008-05-15
Did you launch gparted with root permissions?

---

### Post by js_anoop on 2008-05-15
> If you click the /dev/sda partition it should expand and show the other partitions. There is also an option to Edit Partition Table which should show all partitions on sda.

 That didn't work.

> Did you launch gparted with root permissions? 

I've tried that one too. Doesn't work.

---

### Post by MaindotC on 2008-05-15
Does the command "df" recognize the othe partitions?

---

### Post by js_anoop on 2008-05-15
> **strAlan said:**
> Does the command "df" recognize the othe partitions?

Yes it did.

---

### Post by MaindotC on 2008-05-15
I'm going to the Server 2008 unveiling party in Rochester so I have to leave now.  If no one else helps you I'll try and work on it later today.  Hope you're googling!

---

### Post by js_anoop on 2008-05-15
> **strAlan said:**
> I'm going to the Server 2008 unveiling party in Rochester so I have to leave now.  If no one else helps you I'll try and work on it later today.  Hope you're googling!

Ok. Thanks strAlan.

---

### Post by MaindotC on 2008-05-20
Bump - js_anoop sorry for being afk for so long.  Any progress?

---

