---
title: "Black and white lines - Graphics card issue?"
date: 2011-10-29
forum: New to Ubuntu
---

### Post by BenBowden on 2011-10-29
This is the first time I have install linux as the only OS on a computer. Apart form virtual box.



I have a HP e-Vectra, Pentium III (Designed for Windows 2000, Windows NT 4.0)

I have installed Lubuntu.

**My problem is that when i boot the computer. It looks like it should be loading the OS the screen, but is made up from black and white bars.**

I can just about see where the Lubuntu text would be and the loading "dots".

I would like to see if there was a fix to this problem.



Here is some information that might help you:

sudo lshw -C display

*-display UNCLAIMED
description: VGA compatible controller
Product: 82810e dc-133 (CGC) chipset graphics controller
vendor: intel corporation
physical id: 1
bus info: pci@0000:00:01.0
version: 03
width: 32 bits
clock: 66mhz
capabilities: pm vga_controller bus_master cap_list
configuration: latency:=0
resources: memory:e8000000-ebffffff memory:e8000000-effffff

(To get to a the command line I had to turn the power off so it would boot into safe mode and then i can access ubuntu command line fine. (Without the black and white bars problem) )



Thanks,

Ben.

---

### Post by Rex Bouwense on 2011-11-01
Just a few questions to get a little bit of information.
Did you install Lubuntu 11.10 or an earlier version on your box?  
You never did mention how much RAM you have not that it makes too much difference because Lubuntu can run with a lot less RAM than Ubuntu.
Did you run the md5sum of the downloaded ISO before you created the bootable CD or flash drive?  
If you used a CD did you burn at the lowest speed possible?  
Did your box run Win 2000 before you installed Lubuntu?
Did you try Lubuntu on the CD or flash drive before you installed it?  Did everything work then?

---

### Post by BenBowden on 2011-11-06
On this computer i have installed Lubuntu 11.10 (The latest one)

Do you know the command to show how much RAM the computer has in ubuntu. (I can't remember what it was)

Whats does md5sum mean?

I used a CD and i burned at the one speed that i could burn it at. (There was no choice.)

It ran windows 2000, but a couple of years ago i install windows xp. (It ran XP ok was slowish.)

I used the live CD and booted from the CD. It was very slow, but it did run. (It failed to install though.) So i used the minimal install CD and used commands to download the minimal install for lubuntu.


Thanks :)

---

### Post by amjjawad on 2011-11-06
> **BenBowden said:**
> Do you know the command to show how much RAM the computer has in ubuntu. (I can't remember what it was)

To make it easier for you, you can use a GUI Program/Application for that job.
System Monitor in Ubuntu and Task Manager in Lubuntu.
You can have them both too but one should be enough.
Check the Screenshots attached :)

Terminal Command:
```
top

```


> Whats does md5sum mean?

[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

This is very important and a must-do step IMHO :)


> I used a CD and i burned at the one speed that i could burn it at. (There was no choice.)
What program you have used?

---

### Post by vicshrike on 2011-11-06
For ram : free -m

For md5sum:

[http://en.wikipedia.org/wiki/Md5sum](http://en.wikipedia.org/wiki/Md5sum)

---

### Post by amjjawad on 2011-11-06
> **vicshrike said:**
> For ram : ```
free -m
```

Yes, this one is much better, thanks :)

---

### Post by BenBowden on 2012-01-19
Thanks for all the help but i ended up installing lubuntu on another system and works great. :)

---

