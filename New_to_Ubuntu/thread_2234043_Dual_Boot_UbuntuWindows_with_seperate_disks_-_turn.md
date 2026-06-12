---
title: "Dual Boot Ubuntu/Windows with seperate disks - turn unused disk off"
date: 2014-07-12
forum: New to Ubuntu
---

### Post by Clemens_Wolff on 2014-07-12
Hello everyone,

i started working with a ubuntu server OS a few weeks ago and I really enjoyed it. After some reading I thought about changing from Win to Ubuntu on my laptop as well - it's a Thinkpad X230. Unfortunately there are some programms i need that only run under Win. Sometimes i also like to game so i can't completely delete Win and thought about a dual boot system.

As my SSD only has 240GB storage space I don't want to host both systems on the same disk - under Win i already use 85% of it's capacity. My laptop gives me the opportunity to add another mSata SSD and I thought about buying a small one for hosting Win. The mSATA SSD shouldn't be used unter Ubuntu - I want the OS to be completely seperated.

I could then have the following setup:
SSD 240GB: Ubuntu only
mSata SSD 120GB or 64GB: Win only

As the OS will be completely seperated I was wondering if the unused ssd will automaticly be switched off to save me some battery life. Is there anyone who has already tried it?

Thanks in advance

---

### Post by Bucky Ball on 2014-07-12
Just wondering why you want to have the two OS's seperated. :-k

My personal preference would be to install Win on a 40Gb partition on the 120Gb SSD, Ubuntu on a 25Gb partition right next to it and create shared data partitions with the rest of the drive and the 240Gb drive (240Gb also good for backups as it is a physically separate drive if the other dies ...

To your original question: no, the other drive will not be switched off. You'd need to unplug it. Sure it has power-saving built in and there's no hard drive to stop spinning. SSDs use little power even when you're using it for data transfer ...

---

### Post by ajgreeny on 2014-07-12
> **Bucky Ball said:**
> Just wondering why you want to have the two OS's seperated. :-k

My personal preference would be to install Win on a 40Gb partition on the 120Gb SSD, Ubuntu on a 25Gb partition right next to it and create shared data partitions with the rest of the drive and the 240Gb drive (240Gb also good for backups as it is a physically separate drive if the other dies ...

To your original question: no, the other drive will not be switched off. You'd need to unplug it. Sure it has power-saving built in and there's no hard drive to stop spinning. SSDs use little power even when you're using it for data transfer ...
+1
I totally agree with this as the best arrangement for that hardware setup.

The only possible advantage of of keeping the OSs separate is to have the bootloaders of each OS on a different drive, rather than both being booted through grub on the primary drive, but having had dual boot systems for about 6 of the 9 years that I've been using Ubuntu and never having had any problem at all with grub, I see no good reason to move away from the suggested partition arrangement shown by BB.

---

### Post by Mark Phelps on 2014-07-12
I've got multiple OSs on my desktop and each has its own drive.  I personally have found this to be the best arrangement as I can do bootloader updates on any of the OSs without affecting the others.  Also, each of the drives is then bootable on its own, and I have found that to be convenient. Yes, I know it's a personal preference, but since you're using two SSDs, I would recommend going the way you planned -- with each OS on its own SSD.

---

### Post by Clemens_Wolff on 2014-07-12
If i'm right the data partition needs to be formatted as NTFS for both systems to be able to access it, right? But there isn't much data that needs to be accessible from both OS - i use some programms from uni on windows but everything else should be done via ubuntu. And there's a performance hit using NTFS under ubuntu right? That's why i thought about completely seperating them.

But I do see your point about the data/disk redundancy.

---

### Post by Bucky Ball on 2014-07-12
In that case, use the rest of the 120Gb OS SSD as an NTFS storage partition and the 240Gb EXT4. With 40-50Gb for Win (maybe less, not sure how much just the install needs) and 20Gb for Ubuntu (keep your personal data elsewhere) that leaves about 40Gb. I did read somewhere it is best to leave some free space on an SSD to extend life, but I have no idea if there's truth in that. 

You could put your Ubuntu /home partition on the entire 240Gb EXT4 partition. Super-fast system. OS on one drive, data on the other. 'Back in the day', pre- the speeds hardware can achieve now, it was the only way to go. Still makes sense, especially with regular HDD and for intensive audio/video production/editing. ;)

---

### Post by Mark Phelps on 2014-07-13
>  i use some programms from uni on windowsWhat? This doesn't make sense as Linux apps will not run in Windows.

---

### Post by at_first_light on 2014-07-16
Separating operating systems is a great way to avoid head-aches down the road. I'm not sure if the 2nd drive would be turned off to save power, but I wouldn't expect so. The one concern I would have is whether your laptop supports selecting which hard drive to boot from in it's quick-boot menu?

---

