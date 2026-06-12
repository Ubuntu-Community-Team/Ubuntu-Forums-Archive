---
title: "Accidentally deleted partion is there a fix?"
date: 2008-07-28
forum: New to Ubuntu
---

### Post by Lateforgym on 2008-07-28
Hi,

I was trying to delete the 2 partitions in my USB flash drive in windows by going to Admin tools>Computer management. I accidentally hit Delete partition on my second HDD. Did I lose everything or can I get the data back?

---

### Post by spupy on 2008-07-28
Try the program **TestDisk**. It saved my partitions twice.
Your data is probably not deleted - just the information about the partition. If you haven't used your USB since the accident, TestDisk should be able to locate the deleted partitions and restore them.

---

### Post by coffeecat on 2008-07-28
The third-party Windows GUI partition manager that I use (Acronis) has a commit button and a partition selected for deletion is only actually deleted after you hit commit. So that's a 2-stage process: 1 delete, 2 commit. This is true for Gparted in Ubuntu and (as far as I remember) all the other GUI partition tools I've used in linux.

Are you sure the partition has really been deleted? I haven't used the utility in Admin Tools > Computer Management for a long time, so I can't remember. But I'd be surprised if even Microsoft would make such a design blunder as to omit a commit or 'are you sure?' step to such a destructive command.

---

### Post by Lateforgym on 2008-07-28
"I'd be surprised if even Microsoft would make such a design blunder as to omit a commit or 'are you sure?' step to such a destructive command. "

You not alone. I simply wanted to delete the partition I made through linix on my USB, so I did it through windows. Problem is that when you do it through the method I said above, you have to scroll down I didnt notice that I was deleting the partition from my secondary HDD. Yea, its that easy. I suspect it might ask "Are you sure" if it was your C: drive. The good news is that there appears to be programs to recover the deleted partition info, yet so far these programs cost a lot of money. One program play a game where it would search everything, after a lot of time, ask if you want to recover the deleted partiton, then suddenly says "This option is not available in the Demo version"...Gee thanks for wasting my time when you product description DID say it was in the demo. So far most are too hard to figure out. Im kind of needing something as simple as "Deleted partition found" click next to recover. Some of these programs are too complicated. Anyone know of more simplistic freeware please let me know.

---

### Post by Lateforgym on 2008-07-28
YIPPIE! Its fixed. I used TestDisk which is in Dos but simply uses arrows to navigate. Its very fast if you simply went through (XP Pro) Admin Tools>Computer Management>Disk Management and accidentally deleted a partition. In this case I didnt delete the C drive. I had a second HDD with all my data files, photes, music ect on it. Im very surprised it was that easy to screw this up without warning. Shame on MS. IT managers should pop in a USB stick and see what Im talking about. XP really needs an "are you sure" on this one. Again, perhaps it would do such if I was doing it to the C drive. After some searching on the net Im not the only one who simply wanted to delete a partition on a non-primary drive and failed miserably because I didnt pay close attention to the drive I selected.

I think this is an easy mistake since when you get to the screen, the active window is so small, if you forget to scroll down and take a very close look at what your doing, you can easily think you deleting the partition on a USB, but are actually deleting a HDD partition. I forgot this computer had an extra HDD in it and when I saw two partitions I though they were the two I created on the USB for my Linux install. 

All that really happened if I didnt explain it clearly is that I was planning on a linux distro on a USB. I decided against it and later noticed that my 1GB USB was now only reading 750 MB as a result of formating the USB for the setup. All I was trying to do is get the USB back to a full 1GB by deleting the non-Fat 16 partition.

TestDisk worked fast and was very simple for this fix. Like 5 minutes vs. the hours some of the FBI type programs wanted to spend date mining for every bit of data and every file I may have lost. I used about 6 Demo programs throughout the night and kept stopping them part way. Some of the other were not intuitive. For example one very popular one, Recovery Doctor, would tell me it was searching the second HDD (F:), but then would ask if I wanted to recover the C: drive partition. What?? 

Thanks for the Help!!!!:guitar:

---

### Post by bumanie on 2008-07-28
As suggested by spupy, testdisk is the best program to try - it is free and it's open source. More importantly, it works very well. I recovered and rewrote a partition table with it the other day. Get it [here]("http://www.cgsecurity.org/wiki/TestDisk") or if you are still able to get into ubuntu, it's in the repositories > sudo apt-get install testdiskthen type testdisk in terminal to start the program.

PS: Too late, got interrupted while writing and you've fixed it already. Well done

---

### Post by billgoldberg on 2008-07-28
How exactly is this related to Ubuntu or even linux?

There are Windows forums you can ask these things in.

For future reference:

[http://www.google.com/search?hl=en&q=windows+support+forum&btnG=Google+Search](http://www.google.com/search?hl=en&q=windows+support+forum&btnG=Google+Search)

---

### Post by coffeecat on 2008-07-28
**Lateforgym**, thanks for posting your follow-ups. Most interesting and I am sure appreciated by many - despite the grumpy (and unnecessary) post that precedes this one.

> **Lateforgym said:**
> I suspect it might ask "Are you sure" if it was your C: drive. 

I'm sure you're right. I read somewhere that although the command 'format C:' would work in Windows 3.1 (or thereabouts) - oops! :wink: it's been disabled in XP.

Spoilsports. :lol:

---

### Post by spupy on 2008-07-28
> **billgoldberg said:**
> How exactly is this related to Ubuntu or even linux?

There are Windows forums you can ask these things in.

For future reference:

[http://www.google.com/search?hl=en&q=windows+support+forum&btnG=Google+Search](http://www.google.com/search?hl=en&q=windows+support+forum&btnG=Google+Search)

TestDisk is part of the Linux System Rescue CD - a life saving CD anyone should have!

---

### Post by billgoldberg on 2008-07-28
> **spupy said:**
> TestDisk is part of the Linux System Rescue CD - a life saving CD anyone should have!

I know, but most windows problems like that can be fixed by some sort of linux tool.

The absolute beginners forums is for people having problems with *buntu.

---

