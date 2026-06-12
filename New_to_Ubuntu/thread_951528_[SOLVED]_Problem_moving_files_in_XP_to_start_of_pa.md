---
title: "[SOLVED] Problem moving files in XP to start of partition"
date: 2008-10-18
forum: New to Ubuntu
---

### Post by spocksbeard on 2008-10-18
I'm trying to shrink the size of my XP partition so I can dual boot Ubuntu alongside it without loosing all of my Windows programs and settings etc. 

I've removed everything I can onto a portable drive and uninstalled all the programs I no longer use and tried to defrag the drive so I can decrese the partition size without loosing anything. This worked pretty well, although there are still some "contiguous files" towards the end of the partition which I'm assuming would be lost if I resized the partition. Is there any way to manually move these files to the start of the drive or will repeated de-fragging eventually do the trick?

Attatched is a screenshot showing the defrag screen.

Thanks in advance

---

### Post by Duck2006 on 2008-10-18
Try de-fragging two or three times to see if the files are moved.

---

### Post by niteshifter on 2008-10-18
Hi,

What can also help is to turn off System Restore - it parks it's files at the end of the disk. May also help - if you've 512MB of RAM or more - is to turn off Virtual Memory (that's most, if not all of the green section). Turn them back on when you're done repartitioning / installing.

---

### Post by spocksbeard on 2008-10-18
Thanks for the quick reply. 

I've run defrag 4 times since my last post and the thin blue line has moved up but the thick line hasn't moved at all.

---

### Post by Herman on 2008-10-18
:) It never hurts to defrag Windows, but actually the Ubuntu installer's partitioner in the Live 'Desktop' CD is quite capable of resizing your Windows partition regardless of it's state of fragmentation. :)

---

### Post by spocksbeard on 2008-10-18
> **niteshifter said:**
> Hi,

What can also help is to turn off System Restore - it parks it's files at the end of the disk. May also help - if you've 512MB of RAM or more - is to turn off Virtual Memory (that's most, if not all of the green section). Turn them back on when you're done repartitioning / installing.
OK so I've turned off system restore and virtual memory, rebooted and run the defragger again. Its a little better but the thick blue line is still there(see attatched pic).

---

### Post by arpanaut on 2008-10-18
I've had great success with this utility on 4 different machines, getting the files to the very front of the disk.  On one old and troublesome drive I had to run it in safe-mode and although it took a long time it worked wonders.  Read the documentation, and back up improtant data first.  Hope it works as well for you as it has for me.

[http://www.kessels.com/Jkdefrag/](http://www.kessels.com/Jkdefrag/)

P.S. The default settings worked fine for my purposes... moving files to front of drive.

---

### Post by arpanaut on 2008-10-18
huh?

---

### Post by spocksbeard on 2008-10-18
Thankyou sooo much, it worked perfectly :)

---

### Post by arpanaut on 2008-10-18
Glad to hear that!
Good Luck with the install.

---

### Post by spocksbeard on 2008-10-18
All seems to be going well, wish I'd known the installer had a partition changer within it but oh well.

Quick question, what mount point should I use for 
- The main Ubuntu partition (where the OS will live)
- The swap partition
- An ntfs partition I want to share between Ubuntu and Windows

Any help greatly appreciated as I'm sitting at the screen of my laptop looking blank and scared as I can't find a clear answer anywhere.

---

### Post by Duck2006 on 2008-10-18
When partitioning use

/ as the root partition (where ubuntu lives) 10 to 15Gb
swap partition as swap partition             1Gb
if you want a home partition then make one to (as if you have to reinstall you still have all your settings)            what size you need.

---

### Post by spocksbeard on 2008-10-18
Just to be clear, I need to make the OS live at mount point /, the swap partition doesn't have a mount point and the shared partition mount point /home?

As I had to reduce the size of my existing XP partition do I need to set a mount point for it?

---

### Post by Duck2006 on 2008-10-18
> As I had to reduce the size of my existing XP partition do I need to set a mount point for it?

No it's not need.

---

