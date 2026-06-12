---
title: "[SOLVED] Linux From Scratch-Question Preparing Hard Drive"
date: 2008-07-24
forum: New to Ubuntu
---

### Post by andrewt522 on 2008-07-24
I just discovered Linux From Scratch and thought it would be a good way to learn Linux.  That said, I have been using Ubuntu for a little over a month and am still learning basics.  For example, I never partitioned a hard drive until I set up my first dual boot.  I was successful, but I used the GUI that comes with the install, and know nothing about fdisk.

In order to play with Linux From Scratch, I got my hands on an old Pentium II, which contains a unpartitioned hard drive with Windows XP.  I tried to partition using fdisk, and was getting close, but couldn't close the deal.

Should I prepare the hard drive (i.e. format) before I partition or will setting partitions take care of that for me?  Is there a recommended resource?  Does my lack of knowledge on this basic step disqualify me from even trying this :) (be nice)?

---

### Post by Potatoj316 on 2008-07-24
If you partition the HD you can then choose what filesystem to format to.  If your going to install something like Ubuntu it will partition and format for you.

Also linux from scratch is kind of difficult, are you sure your ready?

---

### Post by andrewt522 on 2008-07-24
In other words, the partition will format for me, yes?

No, I'm not sure I'm ready, but I have the time, will and a computer to break!:lolflag:

---

### Post by Potatoj316 on 2008-07-24
What are you using to partition?  If you are using gparted it will make you choose a filesystem.  If your using fdisk you will have to format manually.

---

### Post by andrewt522 on 2008-07-24
I was trying to use fdisk.

---

### Post by louieb on 2008-07-24
tldp.org has a how to fdisk. Be careful when you Google fdisk. MS has an fdisk program too. Although close the Open source version and the MS version arn't the same. Google **Linux fdisk**  Fdisk is a good program but it doesn't care if you ask it to do something stupid or illogical. If it can it will do just what you tell it to do.

At least GParted has some smarts built in to keep you from doing stuff to your partitions that make no sence.

---

### Post by andrewt522 on 2008-07-24
Thanks, louieb!  Very helpful!

---

### Post by andrewt522 on 2008-07-24
First, again, many thanks to louieb!  I found this page:

[http://tldp.org/HOWTO/Partition/fdisk_partitioning.html](http://tldp.org/HOWTO/Partition/fdisk_partitioning.html)

I was very close last night!  Two things I got from this tutorial:

1) I didn't understand disk geometry.  This article explains how to figure out the size of the partition.

2) I was setting the partitions correctly, but I didn't follow through and complete them by using "p" to show my work and "w" to complete the process.

I'm sure there's more here that will help me.  But tldp.org is a great resource.

Thanks again!

---

