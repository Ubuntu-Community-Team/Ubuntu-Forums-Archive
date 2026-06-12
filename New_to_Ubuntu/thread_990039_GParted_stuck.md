---
title: "GParted stuck?"
date: 2008-11-22
forum: New to Ubuntu
---

### Post by RussW210 on 2008-11-22
I just picked myself up a 1TB external hard drive.  I want to reformat it to NTFS.

So, I downloaded GParted and it says I have two partitions on the drive:

/dev/sdb1 - Filesystem = unknown
/dev/sdb2 - Filesystem = hfc+

I know my computer was using sdb2 to save data.  However, I wanted to reformat sdb2 to ntfc.  So, I reformatted it and am on the "Applying pending operations" window with this bar that has been moving back and forth for 12 hours.  It seems to be hung up on "set partitiontype on /dev/sdb2" action.  Actually, I have no idea if it is actually doing anything.

Now I know my external HD is large and this could take a while.  I have seen ranges of how quickly this could take from other commenter's.  I am aware that Windows has a quick format (I have a Windows laptop but I am running GParted on my Linux Ubuntu 8.10 Desktop) and that only takes a few minutes.  However, I can't cancel this formatting because of an error that comes up saying "I could cause SEVERE damage to my disk if I cancel the operation."  Plus, I don't think I want to format my HD on Windows if I will only be using it on my Linux Computer.

So, I am stuck here waiting.  Does anyone have any idea how long this process should take?  I really would like to know if I am waiting here for nothing when I could be doing something else to get this to quickly work.

Thank you everyone for any help/peace of mind.

---

### Post by buyyourall3 on 2008-11-22
[size=5]It Is A Mini [/size][[size=5]Pen Interview Recorder[/size]](http://www.buyyourall.com/1169_Spy-camera-pen.html)[size=5]. [/size][[size=5]Pen Camera[/size]](http://www.buyyourall.com/1169_Spy-camera-pen.html)[size=5] And Recorder , [/size][[size=5]Pen Digital Video Recorder With Camera[/size]](http://www.buyyourall.com/1169_Spy-camera-pen.html)[size=5], Ideal For Both [/size][[size=5]Spy Camera[/size]](http://www.buyyourall.com/1169_Spy-camera-pen.html)[size=5] & Hidden Camera, Small Enough To Conceal Almost Anywhere! Wherever You Place Your Mini Camera, Youll Know For Sure That You Will Never Miss Anything.A .Record Live Performance And Lecture For Enthusiast Learner And Student;B. Police Can Use It To Law Enforcement;C. Lawyers Can Used It To Collect Evidence;D. Reporter Can Used It To Interviewed In Special Occasion;E. For Stealth Surveillance[/size][[img=543,110]http://www.buyyourall.com/syssite/home/shop/1/pictures/newsimg/1225508621.jpg[/img]](http://www.buyyourall.com/1169_Spy-camera-pen.html)

---

### Post by taurus on 2008-11-22
If you only want to use that harddrive with Linux, then why are you formatting it to ntfs?  Use ext3 filesystem since it's much better.

---

### Post by RussW210 on 2008-11-22
Can ext3 be used safely in Windows and Mac?  I really just need to store files bigger than 4GB so I can't use FAT32...

---

### Post by Kellemora on 2008-11-22
Hi Russ

I don't know about MAC's but all of our data and their backups are stored on EXT3 drives and used by Windows machines all day every day.  If anything it's a lot faster than NTFS and you don't have to worry about defragging either.

I may not be explaining this right, but in NTFS data is stored like beads on a string.  So if you add to a document, that added on part is stored on another bead after all the other beads.  Thus the file is in separate areas on your hard drive.
On EXT3, files are stored in like pigeonholes.  If you add to a file and it won't fit in the pigeonhole it came out of, it's moved to two or more sequential pigeonholes somewhere else on the drive but kept all together as a contiguous file.
The hole it came out of is reused for another smaller file.

Its for this reason that you do not need to defrag an EXT3 drive!

However, if you do defrag, all it does is move the pigeonholes together instead of letting them be spread apart all over the drive.  This can be good or bad depending upon how you look at it.

I think, often used files are stored near the heads riding area and seldom used files are parked far away from the heads riding area.  In other words, files used a lot are often moved from one pigeonhole to another to speed up access times.  But don't quote me on that, I'm not that sure that's how it's done.

TTUL
Gary

---

