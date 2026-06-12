---
title: "fdisk"
date: 2008-10-13
forum: New to Ubuntu
---

### Post by i_have_a_sempron on 2008-10-13
Been having problems with my hard drive and I was finaly able to boot up a gparted live cd. With gparted, I partitioned my hdd into three sections. I have no filesystem on any of them. I am using a Slax Livecd to work with cfdisk and it does display my hdd and partitions but nothing else on my computer will. I need to reinstall ubuntu on my computer but when i try all i get is buffer i/o errors on my logical blocks. I was wondering if anyone would know what i need to do?

---

### Post by Orange_and_Green on 2008-10-13
Hello i_have_a_sempron, it's me again :)

I'm sorry to tell you that at this point, it really looks to me as though your disk (or the disk controller) is physically failing...

To make sure, one thing that maybe is worth trying is extracting the disk from the computer and inserting it into an IDE*-to-USB adapter, as these things are very cheap. That way, you an easily plug your disk into another computer and see if you can read/mount/partition/format it from there.

Good luck :KS

*(or SATA, depending on whether your disk is IDE or SATA of course, but you mentioned the laptop is rather old so I'd bet on IDE)

---

### Post by i_have_a_sempron on 2008-10-13
Yea thats what im afraid of is hard drive failure. My tech guy at school has all the ide - usb adapters and what not, so im going to hit him up and try to figure this all out. Thank you lots for all your help!

---

