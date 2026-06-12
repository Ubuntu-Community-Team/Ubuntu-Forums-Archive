---
title: "Can Ubuntu read and write on an HFS Plus partition?"
date: 2008-08-23
forum: New to Ubuntu
---

### Post by dnns123 on 2008-08-23
Heres the problem:
I want to convert my Ubuntu into 64-bit and my HDD is nearly full.
My bro has an external HDD for his MAC, but it's in HFS+. Can Ubuntu read and write on HFS+ so I can do the transfer?

---

### Post by coffeecat on 2008-08-23
Ubuntu can read hfs+ filesystems, but not write to them. You'll have to find another external medium to write to.

**Edit:** just found hfsutils and hfsutils-tcltk in Synaptic. It seems that hfsutils has a utility to write to hfs volumes from the command line. But I'll leave you to read man hfsutils and work out what on earth it is you have to do. :wink:

---

