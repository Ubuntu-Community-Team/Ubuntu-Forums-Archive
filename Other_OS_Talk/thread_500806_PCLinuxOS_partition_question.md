---
title: "PCLinuxOS partition question"
date: 2007-07-14
forum: Other OS Talk
---

### Post by Stew2 on 2007-07-14
Hi all! Does anyone know how I can get rid of my XP partition and use the space for my PCLinuxOS install? I have a rough idea how to do it in ubuntu but I'm not sure how in PCLinuxOS. I know I could just reinstall PCLinuxOS and let it use my whole hard drive, but is there a simple way to do it without reinstalling? Thanks in advance! :D

Regards,
Stew2

---

### Post by Stew2 on 2007-07-14
I was just checking out the administration/control center thingy and there is a partition manager there. Do you think I could just unmount/ delete the XP partition and resize my home partition? Sounds kind of logical I  think? :D

---

### Post by Epilonsama on 2007-07-14
You should try deleting the XP partition and expanding your PCLOS partition, but you need a partition tool that doesn't mount your hd, ill recommend Gparted live CD.

---

### Post by smoker on 2007-07-14
> **Stew2 said:**
> I was just checking out the administration/control center thingy and there is a partition manager there. Do you think I could just unmount/ delete the XP partition and resize my home partition? Sounds kind of logical I  think? :D

if you're using a live-cd this will work, as long as you unmount the partitions involved. Epilonsama's reccommendation of the Gparted live-cd is also a way to go, i use the gparted live-cd for all partitioning i have to do,

best of luck

---

### Post by Stew2 on 2007-07-15
Cool. I could probably use Gparted on the 6.06 live CD then? (I already have one of those :)) Thanks for the replies guys. I think I would have messed it up if I had tried to do it with the partition mounted :).

---

### Post by smoker on 2007-07-15
hi, not to say the gparted on the 6.06 if flawed, but i personally have had problems with it. i have never though had a problem with the 'gparted live-cd'. if you can download and burn a copy of this, it is a great tool to have handy anytime you may need it!
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

best of luck

---

### Post by Stew2 on 2007-07-15
> **smoker said:**
> hi, not to say the gparted on the 6.06 if flawed, but i personally have had problems with it. i have never though had a problem with the 'gparted live-cd'. if you can download and burn a copy of this, it is a great tool to have handy anytime you may need it!
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

best of luck

Thanks for the link. Small download so I think I will go for it :D. Thanks again for the help!

---

### Post by Stew2 on 2007-07-15
Heh heh. I ended up screwing it up and reinstalling anyway :). I tried using the GParted live CD to delete my NTFS partition and stretch my home partition. Deleting the XP partition went fine but then I had a bunch of unallocated space at the front of the drive. Tried everything I could think of to move or stretch the home partition to use this space. Couldn't figure it out so I just did a clean reinstall. Only takes 20 mins or so anyway so it was no great loss. End result is the same anyway, got rid of XP. :D

Regards,
Stew

---

