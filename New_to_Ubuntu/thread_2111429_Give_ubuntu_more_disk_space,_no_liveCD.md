---
title: "Give ubuntu more disk space, no liveCD"
date: 2013-02-01
forum: New to Ubuntu
---

### Post by jaredsliving on 2013-02-01
I've been trying to give ubuntu some more space, since I've only got 200mb left, and I successfully shrunk windows partition down using gparted within ubuntu, but I can't figure out how to give unbuntu the unallocated space, is there anyway I can give ubuntu the space without having to use a liveCD, because I installed ubuntu using a usb, and I've needed to use that usb after, so I reformated it, so is there anyway I can do this within windows or something? Any help would be much appreciated.

---

### Post by offgridguy on 2013-02-01
> **jaredsliving said:**
> I've been trying to give ubuntu some more space, since I've only got 200mb left, and I successfully shrunk windows partition down using gparted within ubuntu, but I can't figure out how to give unbuntu the unallocated space, is there anyway I can give ubuntu the space without having to use a liveCD, because I installed ubuntu using a usb, and I've needed to use that usb after, so I reformated it, so is there anyway I can do this within windows or something? Any help would be much appreciated.
If you have a CD drive on your computer, the easiest is probably
download gparted and make a live CD. It is a small download.
You can't edit your partitions while they are in use, which is
why you need the live CD.
The general consensus is DON'T use windows to edit linux
partitions. Why?  I dunno.  I'm sure someone will tell us.

---

### Post by jaredsliving on 2013-02-01
Ok, thanks, I'll see if I can find any blank cds. I was also reading that you can use GParted from a harddisk (here [http://gparted.sourceforge.net/livehd.php](http://gparted.sourceforge.net/livehd.php)) is that a safe alternative if I don't have any cds?

---

### Post by offgridguy on 2013-02-01
> **jaredsliving said:**
> Ok, thanks, I'll see if I can find any blank cds. I was also reading that you can use GParted from a harddisk (here [http://gparted.sourceforge.net/livehd.php](http://gparted.sourceforge.net/livehd.php)) is that a safe alternative if I don't have any cds?
This is something i am not familiar with, so i can't make any
recommendations.
Actually partedmagic is what i use, it contains gparted and more,
it's a handy tool to have for times like these.

---

### Post by sandyd on 2013-02-01
[Gparted can be installed on a USB ;)]("http://gparted.sourceforge.net/liveusb.php")
Though some filesystems (ex. btrfs) can be resized online (while in use), it is generally unsafe to do so.

---

### Post by drawkcab on 2013-02-01
Having a live cd/usb with gparted is a key tool for this sort of thing.  Burn one and you can extend your partition!

---

