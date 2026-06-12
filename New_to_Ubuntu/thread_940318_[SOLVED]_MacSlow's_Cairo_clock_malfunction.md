---
title: "[SOLVED] MacSlow's Cairo clock malfunction"
date: 2008-10-06
forum: New to Ubuntu
---

### Post by eternalnewbee on 2008-10-06
Hi there.
when I run MacSlow's Cairo clock it stops ticking after a short while. Like the batteries are empty...
How can I make it run smoothly (without the need to buy new batteries..:)
Thanks
_________________________
Ubuntu 8.04 Gnome 2.22.2 2.6.24-19-generic
AMD Athlon(tm) XP 899.219 MHz 256 KB
GeForce 7300 GT

---

### Post by EnGorDiaz on 2008-10-06
can you run 
```
cairo-clock
``` in terminal and see the errors you get?

---

### Post by eternalnewbee on 2008-10-06
No error message...

---

### Post by eternalnewbee on 2008-10-06
Ok. Now I noticed that showing the seconds messes things up. When the seconds are not displayed it works fine.

---

### Post by eternalnewbee on 2008-10-06
And now I noticed that it got stuck at quarter past and suddenly jumped to 20 minutes past. I really want it to work...

---

### Post by kk0sse54 on 2008-10-06
Right click on the clock and click on properties. From there there should be a slider under Animation Smoothness that you can play around with to adjust the smoothness. Also make sure that you have compositing enabled either by using compiz or enabling it in your xorg.conf

---

### Post by eternalnewbee on 2008-10-07
Thanks C!oud. I think it's working now. I adjusted the roughness to roughest ( that sounded strange...), and seems to be workimg.

---

