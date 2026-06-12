---
title: "Dual boot on a well-used SSD"
date: 2014-03-08
forum: New to Ubuntu
---

### Post by gary-garyfuller on 2014-03-08
I have had a scratch around some of this massive forum, but haven't found an answer/solution to my question.
I have tried Linux with the live cd and like it, but would like to see how it performs when installed on a permanent basis.
I want to dual boot win7 and Ubuntu. I have a static pc with a 228 gb SSD as the primary hard disk. At the moment the OS installed is W7 Ultra. The drive is massively fragmented but does have around 165 gb free space.
Defragging ssd drives is not recommended by the manufacturer. Is there a way to get around this problem, or do I have to go to the expense of buying a new SSD?
I would be most grateful for any replies. :P

---

### Post by mikewhatever on 2014-03-08
see post #4 for correct info ;)

---

### Post by Mark Phelps on 2014-03-08
Have you tried shrinking the Win7 OS partition using Disk Management?  IF not, do that first and see how much space it will let you recover.  IF it is stubborn about that, try the tips in the linked post:  [http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/]("http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/")

---

### Post by whitesmith on 2014-03-08
> **gary-garyfuller said:**
> I have had a scratch around some of this massive forum, but haven't found an answer/solution to my question.
I have tried Linux with the live cd and like it, but would like to see how it performs when installed on a permanent basis.
I want to dual boot win7 and Ubuntu. I have a static pc with a 228 gb SSD as the primary hard disk. At the moment the OS installed is W7 Ultra. The drive is massively fragmented but does have around 165 gb free space.
Defragging ssd drives is not recommended by the manufacturer. Is there a way to get around this problem, or do I have to go to the expense of buying a new SSD?
I would be most grateful for any replies.:PDefragging SSDs is never necessary, regardless of the OS, and may actually damage the device. Tracks, sectors, heads, cylinders -- all of these are just metaphysical concepts with SSDs because these devices are simply a RAM-emulated HDD. On physical HDDs latency can be noticed when the drive is badly fragmented. On emulated HDDs (SSDs, in other words) fragmentation never leads to latency because memory is accessed directly. It takes no more time to access data on a fragmented SSD than one that isn't. Don't ever attempt defragmentation on an SSD. Doing so wears NAND gates and eventuality leads to device failure. Wikipedia has some choice words on the subject([http://en.wikipedia.org/wiki/Ssd](http://en.wikipedia.org/wiki/Ssd)).

---

### Post by gary-garyfuller on 2014-03-09
Thankyou all for your fast replies, I will get down to some serious reading and get back.
Thanks again.

---

### Post by gary-garyfuller on 2014-03-09
After some speed-reading, I followed the instructions for shrinking a partition. I now have a 44gb unallocated space on my SSD.

I downloaded the Ubuntu 13.04 desktop ISO image, size 823,132 KB, when I open it in Windows with UltraISO it contains one folder Named EFI size 2245 KB. :wink:


TIA

---

### Post by mikewhatever on 2014-03-09
Next step after downloading an ISO is to prepare the installation media, DVD or flash drive. Apparently, UltraISO is not the right tool for that, instead, check out the howtos below:
[DVD]("http://www.ubuntu.com/download/desktop/burn-a-dvd-on-windows")
[USB]("http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows")

You might also want to know that 13.04 has reached end of support in January. The supported releases are 12.04 and 13.10. Both are available from [http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop).

---

### Post by gary-garyfuller on 2014-03-10
I have decided to give Linux the "go by" for the time being. Messing around with the live cd, I seem to have managed to wipe my windows partition.

---

### Post by Vladlenin5000 on 2014-03-12
> **gary-garyfuller said:**
> I have decided to give Linux the "go by" for the time being. Messing around with the live cd, I seem to have managed to wipe my windows partition.

Yeah, if you mess around far enough as to open a partition manager, select your Windows partition(s) and explicitly ask&confirm the removal of the selected partitions the software you happily and swiftly do just that. Likewise, if you mess around as far as to open a file explorer and start deleting stuff in your internal hard drive the system will happily proceed whenever possible.

There are no other scenarios where an entire partition is wiped **in a live session**.  Wiping such partitions can happen during **installation **when you select the option "Use the entire drive" (or something like that), duh... Again, it's the system following your explicit orders.

---

