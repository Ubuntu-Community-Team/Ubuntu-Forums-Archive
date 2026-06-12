---
title: "Problem in booting through ubuntu"
date: 2008-08-28
forum: New to Ubuntu
---

### Post by kachamanandrao on 2008-08-28
Hello,
  I have loaded Ubuntu (after windows Vista) in my AMD Athlon PC with 768 MB RAM with suitable AGP graphics card. After booting and selection of ubuntu operating system, the system just hangs while getting the starting screen / some other stage later after booting.
  This I have observed only when the graphics card present in my system. Without graphics card, my system boots in ubuntu perfectly and works properly. Please suggest solution to my problem, if any?

---

### Post by DemonBob on 2008-08-28
What type of graphics car? Nvidia? Ati? 

When it gets to the spot where it "hangs" can you do an ctrl+alt+f3 do you get a command prompt?

---

### Post by Separ on 2008-08-28
Can you boot into recovery mode? It is usually the second entry in the Grub menu.

Once in there type ```
lspci -v | grep VGA >> /media/YOURDISK/lspci.txt
```
Replacing YOURDISK with the full path to a USB thumb drive or something so that you can save the output to a text file which you can then copy to here.

EDIT: Try what DemonBob suggested first. If it doesn't show, try what I have posted above.

---

### Post by kachamanandrao on 2008-08-28
> **DemonBob said:**
> What type of graphics car? Nvidia? Ati? 

When it gets to the spot where it "hangs" can you do an ctrl+alt+f3 do you get a command prompt?

I have nvidia graphics card.
It hangs not exactly at the same spot. It randomly hangs at different spots every time I boot. I would try ctrl+alt+f3 and come back. Thanks for suggestions

---

### Post by kachamanandrao on 2008-08-28
ctrl+alt+f3 is not working at the spot of hanging.
recovery mode also gives same problem. it hangs after entering user name some times. some other times after entering password. in the recovery mode it goes ahead, and then hangs after booting and working for few minutes.

---

