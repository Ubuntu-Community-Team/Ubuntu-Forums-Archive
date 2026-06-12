---
title: "Newb: Install ubuntu to &quot;hybrid&quot; HDD samsung series 7"
date: 2019-06-19
forum: New to Ubuntu
---

### Post by edward-j-rock on 2019-06-19
Hi all. As it states in the title I have a Series 7 samsung (Gen 3 core I7) with a 1TB hybrid HDD. 8G of this drive is SSD and is a separate partition. Win 10 automatically installed and utilized the SSD partition. I put my initial ubuntu install entirely on the 8G SSD. My question is two fold: Is there a best practice when installing linux to such a drive? And if not, should I install ubunto to the analog drive portion and specify the SSD for page swap or keep it where it is on the SSD? This is a secondary pc for me so there are no worries of losing data. I  wish to go full bore linux and remove any vestigial windows and see what this thing can do.


Separately, if I were to format the whole HDD, how do I direct ubuntu to recognize and partition the SSD? 

Thanks in advance!!
Ed

---

### Post by kpatz on 2019-06-19
On the series 7, the SSD is integrated on the motherboard and separate from the HDD (unlike a true hybrid HDD which has flash onboard for caching purposes).

I wouldn't put swap on the SSD, as excessive writes can wear down the SSD cells prematurely.  Maybe put the OS filesystem (/) on the SSD and create partitions on the HDD for /home, /var and swap.  That way the OS will boot fast from the SSD, and the places were larger, more frequently updated files tend to reside (/var and /home) can go on the HDD.

(Edit: I added to create a swap partition since Ubuntu 18.04 by default creates a swap file in the root, which would end up on the SSD in this scenario unless the installer is smart enough to avoid doing this).

---

### Post by edward-j-rock on 2019-06-20
Thanks Kpatz. Since I already installed to the SSD, it is likely that the swap file is also there. Can I easily move this or will I need to reinstall the whole kit and kaboodle? I already may be answering this if there are no partitions that I can use...:bangtard:

---

### Post by kpatz on 2019-06-20
The command ** swapon --summary** will tell you where any swap file(s) and partitions(s).

There are ways to relocate the swap file even if you don't have a swap partition.  How did you partition the HDD?  Also, how much RAM do you have?

---

### Post by edward-j-rock on 2019-06-24
Sorry for the late reply kpatz,

I left the partitions alone: 3  total, the 8G SSD and then two 500G analog. The wierd thing is WIN 10  called it one contiguous drive. 

IIR I have 12G of ram, I will have to check to confirm.

---

### Post by kpatz on 2019-06-24
Are the two 500G HDD partitions for Ubuntu or Windows?  If Ubuntu, where are they mounted?

With 12G RAM, you could get by with no swap at all, unless you edit videos, large images or open 50 tabs in a browser all the time.

Win 10 probably defaulted to using the SSD as a Readyboost cache rather than a regular drive, or a Samsung tool was preinstalled that did something similar.  When I had a series 7 it had windows 7 and Samsung had a tool that used the SSD as a cache to speed up boot and loading of commonly used applications.

---

### Post by edward-j-rock on 2019-06-24
> **kpatz said:**
> Are the two 500G HDD partitions for Ubuntu or Windows?  If Ubuntu, where are they mounted?

With 12G RAM, you could get by with no swap at all, unless you edit videos, large images or open 50 tabs in a browser all the time.

Win 10 probably defaulted to using the SSD as a Readyboost cache rather than a regular drive, or a Samsung tool was preinstalled that did something similar.  When I had a series 7 it had windows 7 and Samsung had a tool that used the SSD as a cache to speed up boot and loading of commonly used applications.

This is exactly what win10 did!! It originally came with 7 so now I remember this. As far as where the drives are mounted, I think they are still for windows since all of my files were still there when I investigated them. I also do not do videos or large images. I might play steam games though. Civ 5.

My schedule is pretty packed these days. It might be a few days before I can get back to it.

---

