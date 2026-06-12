---
title: "Ubuntu installation freezes/fails"
date: 2008-05-08
forum: New to Ubuntu
---

### Post by ALex! on 2008-05-08
Hi!
I've tried to install Ubuntu 5 times, and each time I tried to, the install "wizard" freezed in 15% of progress... The same happened with Xubuntu...
Please help me....

---

### Post by Tatty on 2008-05-08
Is this an install from the Live CD?

It might be a bad burn, it might be worth burning another more slowly to make sure its ok...

1. First check the md5sum of the .iso - [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

2. Burn the CD again with the slowest possible speed your burner can manage - 4x would be good but 10x will do

3. Boot the CD, but before selecting "start/install ubuntu" select the option a few below that "check cd for errors" (or it might be check cd integrity, i cant quite remember)

4. If all of that checks out, then go for another install.

-

5. If it fails again, it might be worth downloading the alternate CD, and seeing if you can install from that.

---

### Post by ALex! on 2008-05-08
> **Tatty said:**
> Is this an install from the Live CD?

It might be a bad burn, it might be worth burning another more slowly to make sure its ok...

1. First check the md5sum of the .iso - [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

2. Burn the CD again with the slowest possible speed your burner can manage - 4x would be good but 10x will do

3. Boot the CD, but before selecting "start/install ubuntu" select the option a few below that "check cd for errors" (or it might be check cd integrity, i cant quite remember)

4. If all of that checks out, then go for another install.

-

5. If it fails again, it might be worth downloading the alternate CD, and seeing if you can install from that.
 
It's a Live install... I have used those Live CDs for other 3 computers and they did work! :???: 
In fact, I installed Kubuntu in that same computer, and it worked....

---

### Post by Tatty on 2008-05-08
Well it could still be a problem with the CD - have a look to see if its got scratched / dirty.  I had a problem with a Live CD failing on me last week, and when I looked at the state of the CD i could see why it was complaining :)


If its not the CD then it could be a problem with the hardware on your machine.  If so its likely to either be RAM or the CD drive itself.  You could try running a memory test on your machine.  Or it might be quicker to just swap over the ram and then the CD drive with components you know work (if you have any spare)

---

### Post by ALex! on 2008-05-08
> **Tatty said:**
> Well it could still be a problem with the CD - have a look to see if its got scratched / dirty.  I had a problem with a Live CD failing on me last week, and when I looked at the state of the CD i could see why it was complaining :)


If its not the CD then it could be a problem with the hardware on your machine.  If so its likely to either be RAM or the CD drive itself.  You could try running a memory test on your machine.  Or it might be quicker to just swap over the ram and then the CD drive with components you know work (if you have any spare)

My CD has no scratches... And my machine works properly :(
 thank you

---

### Post by Tatty on 2008-05-08
> **ALex! said:**
> My CD has no scratches... And my machine works properly :(
 thank you

Have you tried swapping out your components?  Complicated software like OS installs/live cds can often fall over from very slight glitches in hardware which may not be noticeable when using them for more day to day applications.

Though i definately would try using an alternate CD first if I were you.  The Live CD is not flawless, and sometimes only the alternate CD will work.

Beyond this I am out of things to suggest...

---

### Post by spiderbatdad on 2008-05-08
Usually freezing like that is due to hardware detection problems. Consider using some boot parameter by pressing F6 from the grub options screen. Delete --quiet splash from the end of the kernel line and try replacing with noapic nolapic. There are several other boot parameters that are likely to work as well. If you press F1...F6 again after pressing F6 the first time, I believe you will get some information on boot parameters.

Sometimes merely deleting --quiet splash is enough to solve the problem...temporarily. Changes are made permanent by editing /boot/grub/menu.lst after the installation.

---

