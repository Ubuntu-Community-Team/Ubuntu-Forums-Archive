---
title: "Problem After installing PCLinuxOS"
date: 2007-10-30
forum: Other OS Talk
---

### Post by new2*buntu on 2007-10-30
I just installed PCLinuxOS over my Ubuntu 7.10 partition (leaving Mint the way it was) and it overwrote my MBR and installed a new GRUB. I am still able to boot into Mint, PCLinuxOS, and Windows, but whenever I open GParted it always shows the whole drive as unallocated, but I know that there is data because Mint and PCLinux can all be used. Also, would there be any way to make GRUB boot from my Mint partition instead? Please help me fix GParted.

---

### Post by Happy_Man on 2007-10-30
Get a copy of the Gparted LiveCD and use that to fix your problem. 

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

### Post by 67GTA on 2007-10-30
I had the same problem last year when I used the PCLinuxOS installer to partition my hard drive. Gparted wouldn't read the drive anymore. I finally had to use dwipe and use Ubuntu's Gparted via live cd to partition with. I think it has something to do with the way Anaconda labels the partitions.

---

### Post by new2*buntu on 2007-10-30
> **67GTA said:**
> I had the same problem last year when I used the PCLinuxOS installer to partition my hard drive. Gparted wouldn't read the drive anymore. I finally had to use dwipe and use Ubuntu's Gparted via live cd to partition with. I think it has something to do with the way Anaconda labels the partitions.

Could you tell me how to do that?

---

### Post by RAV TUX on 2007-10-30
> **new2*buntu said:**
> I just installed PCLinuxOS over my Ubuntu 7.10 partition (leaving Mint the way it was) and it overwrote my MBR and installed a new GRUB. I am still able to boot into Mint, PCLinuxOS, and Windows, but whenever I open GParted it always shows the whole drive as unallocated, but I know that there is data because Mint and PCLinux can all be used. Also, would there be any way to make GRUB boot from my Mint partition instead? Please help me fix GParted.

At least you got PCLinuxOS to load on your computer, I have never even got PCLInuxOS to boot on my computer. 

I gave up on them a long time ago.

---

### Post by mikewhatever on 2007-10-31
> **new2*buntu said:**
> I just installed PCLinuxOS over my Ubuntu 7.10 partition (leaving Mint the way it was) and it overwrote my MBR and installed a new GRUB. I am still able to boot into Mint, PCLinuxOS, and Windows, but whenever I open GParted it always shows the whole drive as unallocated, but I know that there is data because Mint and PCLinux can all be used. Also, would there be any way to make GRUB boot from my Mint partition instead? Please help me fix GParted.

Could you post the output of sudo fdisk -l from your Linux-Mint. I was wondering if you have such errors there 'Partition 1 does not end on cylinder boundary'.

---

### Post by 67GTA on 2007-10-31
Download Darin's Nuke and Boot for CD, and use it to wipe your hard drive. Then boot with live cd, open a terminal, and > sudo apt-get install gparted

---

### Post by 67GTA on 2007-10-31
I forgot the link [http://dban.sourceforge.net/](http://dban.sourceforge.net/)

---

### Post by new2*buntu on 2007-10-31
> **mikewhatever said:**
> Could you post the output of sudo fdisk -l from your Linux-Mint. I was wondering if you have such errors there 'Partition 1 does not end on cylinder boundary'.
Please see my attached screenshot
[[IMG]http://img508.imageshack.us/img508/6225/fdiskoutputik9.th.png[/IMG]](http://img508.imageshack.us/my.php?image=fdiskoutputik9.png)

---

### Post by SunnyRabbiera on 2007-10-31
have you tried to ask this over at the PCLinux forum yet?
they have a support forum over there.

---

### Post by new2*buntu on 2007-10-31
I have fixed the problem now. I downloaded Linux Mint 4 (beta) and repartitioned the whole drive. No Windows now but it really doesn't matter. (I have been looking for an excuse to destroy it) :)

---

