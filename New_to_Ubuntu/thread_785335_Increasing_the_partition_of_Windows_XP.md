---
title: "Increasing the partition of Windows XP"
date: 2008-05-07
forum: New to Ubuntu
---

### Post by Berean on 2008-05-07
Hi, I've just done a fresh install of 8.04 but have realised that my XP partition is not as big as I would have liked!  I've tried using partition editor to increase the partition - using the live CD - but although I can shrink Hardy, I don't seem to be able to increase XP.  Any ideas gratefully received.  Regards

---

### Post by njparton on 2008-05-08
Correct, gparted can't resize NTFS partitions. 
 
Now that you've shrinked your linux partition you can boot into windows and use the inbuilt windows disk manager to increase the partition size or a 3rd party app such as partition magic.

---

### Post by kansasnoob on 2008-05-08
I managed to do this ONCE! I shout once, because I'm only a few months into Ubuntu and I still break things ;^/

But when I did my first dual boot with win XP and 8.04 w/XP installed first to the entire drive I just let Ubuntu do it's auto-resizing thing and ended up with a very small XP partition. 

After shrinking the Ubuntu partition using the Live CD, I installed ntfsprogs from synaptic and used the ntfsresize tool to increase the size of the ntfs partition while booted into Ubuntu 8.04 (so naturally the XP partition was "unmounted").

It worked fine for me, but as I said ............. I"VE DONE IT ONCE, so try running this idea by some long time users. Feel free to cut-n-paste my idea into any forum! Sometimes I think I just get lucky! Sometimes I do something a second time and break things, so definitely run my ideas past others!

Sometimes my notes are less than complete and my memory may not be 100% correct. You can also check out the ntfsprogs site:
[http://www.linux-ntfs.org/doku.php?id=ntfsprogs](http://www.linux-ntfs.org/doku.php?id=ntfsprogs)

---

### Post by njparton on 2008-05-09
Personally I wouldn't play around with NTFS partitions in linux, it's too risky.

---

### Post by thisiam on 2008-05-09
Gparted should be able to do anything to NTFS partitions, including re size.

[IMG]http://gparted.sourceforge.net/screens/gparted_10_small.jpg[/IMG]

---

### Post by njparton on 2008-05-09
I've heard a few horror stories about this so I tend to play around with NTFS partitions in windows and linux partitions in linux.
 
It just minimises the chances of data loss.

---

### Post by malathion on 2008-05-09
You should back up your data before editing partitions no matter what.

---

