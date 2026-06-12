---
title: "Window7 C:/ in ubuntu"
date: 2012-09-25
forum: New to Ubuntu
---

### Post by SupermanNC21 on 2012-09-25
Hey so i was getting music off my usb when i saw my windows 7 C:/ file in Ubuntu i used WUI from the Ubuntu cd i just wanted to make sure that this want harm my windows files or my ubuntu files i don't know how it got there or if it suppose to be there.

---

### Post by MoebusNet on 2012-09-25
Unless your HDD or partition is encrypted, Ubuntu should be able to see any partition and files that are mounted. This is normal and as designed.

---

### Post by Mark Phelps on 2012-09-25
> **SupermanNC21 said:**
> Hey so i was getting music off my usb when i saw my windows 7 C:/ file in Ubuntu ...
"C:" is not a file; it is a letter assigned to a partition -- which is called a "drive" in Windows.

> i used WUI from the Ubuntu cd i just wanted to make sure that this want harm my windows files or my ubuntu files
If you write to or change files after mounting the "C" partition read/write, you run  the risk of corrupting the Windows file system, as it doesn't deal well with changes made from "outside".  IF you only read files, you won't hurt anuthing.

>  i don't know how it got there or if it suppose to be there.Ubuntu sees all the partitions on any connected drive -- and is supposed to do that.  IT got there automatically.

---

### Post by SupermanNC21 on 2012-09-25
Ah ok thank you guyz i was just alittle worried about that didn't want to mess anything up.

---

