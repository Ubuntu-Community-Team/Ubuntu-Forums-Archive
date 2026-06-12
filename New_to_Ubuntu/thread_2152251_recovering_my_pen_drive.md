---
title: "recovering my pen drive"
date: 2013-06-07
forum: New to Ubuntu
---

### Post by quarkhirad on 2013-06-07
Hi i have been using my pen drive and now all of a sudden i just doesnt get detected. When i type mount it is not listed in their. Hence i type dmesg. In the output it recognized my pendrive as a kingston data traveler. my pen drive is a 32gb kingston usb3.0 pendrive. Now further down it says cannot read partition table. What do i do as i need the files on the pen drive they are very important. Is their some kind of software that i can use to recover my data. Please help me. 


I have attached the dmesg output for your reference. 
[ATTACH]243599[/ATTACH]

---

### Post by Mark Phelps on 2013-06-07
Sadly, I have personally found pendrives (and SD cards) to be very unreliable.  I've had several fail on me, and despite using the best data recovery apps available, I have never been able to recover files from them.

If your pendrive was formatted FAT32 or NTFS, then you will likely have better luck recovering files using a Windows data recovery app -- but it will cost you because the best ones are not free.

If your pendrive was formatted with a Linux filesystem, you can try using Testdisk:  [http://ubuntuforums.org/showthread.php?t=387922&highlight=data+recovery]("http://ubuntuforums.org/showthread.php?t=387922&highlight=data+recovery")

---

