---
title: "How to change file system description?"
date: 2008-07-06
forum: New to Ubuntu
---

### Post by nspur on 2008-07-06
I took the plunge and deleted Vista from my dual-boot system and partitioned the hard disk as a main Linux partition plus swap and a large Dos (FAT32) partition to be shared between the Ubuntu computer and the Windows network. This worked fine.

Then I decided to change the properties of the Dos partition and typed FAT32 for the filesystem. NOW IT WON'T MOUNT

So my question is how to I change the filesystem name so that it will be mountable? And change it to what description?

Any help gratefully received.

Nick

---

### Post by ChameleonDave on 2008-07-06
> **nspur said:**
> I took the plunge and deleted Vista from my dual-boot system and partitioned the hard disk as a main Linux partition plus swap and a large Dos (FAT32) partition to be shared between the Ubuntu computer and the Windows network. This worked fine.

Then I decided to change the properties of the Dos partition and typed FAT32 for the filesystem. NOW IT WON'T MOUNT

So my question is how to I change the filesystem name so that it will be mountable? And change it to what description?

Any help gratefully received.

Nick

Your question is a little confusing.  You mention that it won't mount, but then you speak of "filesystem names" and "descriptions".  I don't get the connection between them.  What do you actually want to do?

When you say that the partition won't mount, but what measured taken by you failed to mount it?

It might be helpful if you posted the output of these various commands:

```

cat /etc/lsb-release
uname -a
sudo blkid
sudo fdisk -l
cat /etc/fstab

```

Open a terminal, and enter each command on its own line.

---

### Post by nspur on 2008-07-06
The problem was the case-sensitivity of Unix names. A simple parted mkfs 6 fat32 sorted it out.

---

### Post by ChameleonDave on 2008-07-07
> **nspur said:**
> The problem was the case-sensitivity of Unix names. A simple parted mkfs 6 fat32 sorted it out.

Perhaps  you could use the "Thread Tools" menu to mark this thread as solved.

---

