---
title: "decrease swap size?"
date: 2008-08-18
forum: New to Ubuntu
---

### Post by bench88 on 2008-08-18
when installing ubuntu 8.04 I created my swap drive size as 100gb.  I'd like to decrease this, how do I decrease the swap size drive?

Thanks in advance!

---

### Post by llama320 on 2008-08-18
gparted will do the trick i should think :)

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

Good Luck

---

### Post by Elfy on 2008-08-18
That has to be the biggest swap I've heard of :) what do you intend to do with the space afterwards?

---

### Post by bench88 on 2008-08-18
change it to a 10gb swap and use the other 90gb as a ubuntu or windows partioned storage space

I'll use the program tonight and let you guys know how it turns out!

---

### Post by Elfy on 2008-08-18
Why do you think you need a 10Gb swap? If you need to hibernate then swap+RAM but I doubt if you'd use half a gigabyte normally.

---

### Post by bench88 on 2008-08-18
ok I'll change it to 1gb swap, I hope this program isn't too hard to use!

---

### Post by drs305 on 2008-08-18
> **bench88 said:**
> ok I'll change it to 1gb swap, I hope this program isn't too hard to use!

No it's fairly straightforward. Remember that gparted can't work on a mounted partition. When you are working on the swap partition, you have to 'unmount' it. Normally in gparted, you go to Partition, Unmount, but since this is a swap partition you would choose "Swapoff".

---

### Post by Elfy on 2008-08-18
No it's easy enough - right click partition you want to change - tell it what to do and hit apply. Obviously I'd make the other partition while you are in there. 

Though I will add that you are dealing with partitions so it is as well to make sure you have backups just in case.

---

