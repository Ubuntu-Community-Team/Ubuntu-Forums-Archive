---
title: "Windows Partition - Error executing batch"
date: 2008-07-17
forum: New to Ubuntu
---

### Post by malexous on 2008-07-17
I am trying to install Ubuntu for the first time on our Dell Dimension 4500. I tried resizing the Windows partition when installing Ubuntu but it gave me an error. I downloaded PowerQuest Partition Magic 8 and when it tried to resize the partition it gave me an error too. I believe the error was executing batch. Can anyone help me? I want to use reinstalling Windows as a last resort because it is unlikely that my dad will let me.

---

### Post by Morpheun on 2008-07-17
First off all, did you mount the disk during your session (I assume you're installing from the live cd)?

If so partitioning it won't really be possible in any sort of easy way. Second, I'm just gonna give you the "Be sure all your data is backed up" warning that I feel compelled to give when questioned about partitioning. The next step would be to turn off the computer and boot from the live cd and use gparted. Partitioning won't work on a mounted disk.

---

### Post by markjensen on 2008-07-17
In addition to ensuring the drive is not mounted, please also boot Windows and do a full scandisk and defrag.

This will ensure that your NTFS filesystem is clean and without weird errors like unclosed file fragments.   A corrupt filesystem should not be adjusted to change parameters like partition end point, because you cannot rely on the data presented until it is repaired.

The defrag should push all the data to the front of the drive, allowing a resizer to shrink without running into data area.   You cannot shrink a fileystem if it is full, or (to my understanding) if there is data at the end of the drive.  Doing so would move the partition end before your file(s), and your files would then exist within and be overwritten by the new ext3 partitions you create.   Bad stuff. :P

---

### Post by kansasnoob on 2008-07-17
Is this Windows Vista perchance?

---

### Post by Sef on 2008-07-17
> I downloaded PowerQuest Partition Magic 8....

Partition Magic and GNU/Linux have been known not to get along well.  It would be best to use another partitioner.  GParted on the Live CD will work fine.

---

### Post by malexous on 2008-07-17
We are running Windows XP Home Edition. I defragmented Windows and checked the disk for errors. I still get the same thing. Error 1529 information mismatch in directory entry.

---

### Post by markjensen on 2008-07-17
Can you boot your Ubuntu CD into LiveCD mode, and post the output of the following:
**sudo fdisk -l**

That will "list" your partitions seen.  I am suspecting we have an ugly overlap or such.

---

### Post by Rhubarb on 2008-07-17
Don't use Partition Magic, it doesn't seem to do what it says on the label.

Instead you may resize your Windows partition by either using the Ubuntu live CD installer, or by going to System --> Administration --> Partition Editor on the Ubuntu live CD.
It works very well, and IMHO it's easier (and cheaper) to use than partition magic, and most important of all, it actually works.

---

### Post by lisati on 2008-07-17
> **malexous said:**
> We are running Windows XP Home Edition. I defragmented Windows and checked the disk for errors. I still get the same thing. Error 1529 information mismatch in directory entry.
There might be some "rubbish" on your Windows partition in its folder(s) for temporary files. The Windows "clean manager" (found on the Programs->accessories menu on some XP systems) will get rid of many (but not all) temporary files. You can also check the temporary files by clicking on Start->Run, entering [code]%temp%{/code] and clicking "OK". The files here can usually be safely deleted without risk of harm.


EDIT: I'd also recommend doing a Windows SCANDISK (or CHKDSK as appropriate) and deleting temporary files BEFORE doing a defrag.....

---

### Post by malexous on 2008-07-21
w00t! I now have Linux on our computer :D

I tried everything you guys suggested...but it didn't work. In the end, what did work I wouldn't have done if you guys hadn't suggested what you did. TuneUp Utilities 2008 was suggested to someone else on Yahoo! Answers. I decided to try it, downloaded the trial and did everything it offered. Then I defraged again. Some Steam files that could not defrag the last 4 times I did it defragged this time and using gparted I managed to resize the partition. 

Thanks to everyone who replied.

Now all I have to do is get the wireless to work...

---

