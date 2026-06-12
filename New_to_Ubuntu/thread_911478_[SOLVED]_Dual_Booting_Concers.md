---
title: "[SOLVED] Dual Booting Concers"
date: 2008-09-05
forum: New to Ubuntu
---

### Post by flamingswrd on 2008-09-05
I have made the move to install Ubuntu to my computer and have freed the necessary hard drive space but as easy as the process of dual-booting sounds, it still worries me. Can someone answer my questions about the process? 
*For reference, I am using the Ubuntu Documentation Guide found [here]("https://help.ubuntu.com/8.04/switching/dualboot-procedure.html")and the Partitioning guide, [here]("https://help.ubuntu.com/8.04/switching/installing-partitioning.html").
*System Config: AMD Turion 64 Mobile 2.41GHz, 2GB Ram, WinXP SP2, 120gb drive

1) In both guides, it recommends/says that I need a swap partition twice my system memory. They are referring to my systems RAM, correct?

2) In one portion of the guide it says that it will erase my hard drive when I re-size the partition and I need to make a backup copy of my data. Is this true? 

3) There a few partitions to create, but how much free disk space is really needed? (I have 44GB left on my C drive, and am wondering if I need to clear up more for programs and such).

I thank you in advance for your assistance and am looking forward to my Linux/Ubuntu experience.

Edit: In case it matters for any reason, I have a 500GB external drive at my disposal. It has around 370GB+ free space and is NOT always connected (usually for backups, file access, etc).

---

### Post by nateperson on 2008-09-05
I pretty recently installed ubuntu and am dual booting with xp.  

1) there are arguments all over the web about how much swap space is really needed.  I did 1.5 * physical ram. For daily regular use... (email, openoffice, internet, movies and such) its been plenty.

2)Its always a good idea to make a back up anytime you make a major system change.  The everything on the new partition will be deleted, but since its resizing you old partition, as long as there's room on the entire physical drive to create a new partition nothing on your old partition should be deleted.  Just the free space taken up by the new partition.

3)  I'm only using 26G of the free space of the partition I've got for linux.  But you need to remember, that the free space you allocate to linux will be pretty much unavailable for windows.  So you will need to leave enough space for your windows installation to work properly...  

If your really concerned, look at wubi.  No repartitioning required, it installs ubuntu into a folder on your c drive and you can boot into it from there...  

Enjoy,

Nate

---

### Post by clinto on 2008-09-05
Yeah, back in the day when ave. RAM size was like 32MB it was a good idea to make swap twice as big.  Now however, I don't think that's the case considering most people have a gig or 2.  I had 512MB for a long time and I never used swap.  However, I usually just give swap a gig.

---

### Post by Therion on 2008-09-05
> **flamingswrd said:**
> 
1) In both guides, it recommends/says that I need a swap partition twice my system memory. They are referring to my systems RAM, correct?
Yes, they are.  I suggest you simply set it to 512MB and be done with it.  The more system RAM you have the LESS likely you are to need swap space.  I'm sure this will positively set some people *right... off...*., but I use what works and don't see the point in letting a default install suck up nearly 3GB of precious hard drive space for swap file!  Please.  We've come a long way since the VM=RAM*1.5 era.

> **flamingswrd said:**
> 2) In one portion of the guide it says that it will erase my hard drive when I re-size the partition and I need to make a backup copy of my data. Is this true?
I can't suggest anyone move or resize partitions without having backups in place, but I've resized many a partition and never lost a single bit of data in doing so.  

> **flamingswrd said:**
> 3) There a few partitions to create, but how much free disk space is really needed? (I have 44GB left on my C drive, and am wondering if I need to clear up more for programs and such).
I split my free space equally between the two OS'es, but if I was forced to, I'd reduce the amount of space alloted to Ubuntu:  It's far less bloated than XP to begin with and less likely to GET bloated.

---

### Post by Shazaam on 2008-09-05
1. Only make a swap partition twice (or larger) than your installed memory (ram) size if you-
 A: Don't have much memory installed (512mb or less).
 B. Are going to suspend/hibernate your pc
2. When you do ANY partition work you should ALWAYS backup your critical files. Things happen sometimes with any operating system. That said, you are relatively safe resizing partitions. When you resize a Windows partition make sure you defragment it first; when you are done with the resize boot Windows and run a disk check (Scandisk, chkdsk, etc).
3. Size is up to you. 10 plus gigs is fine. Ubuntu will run on small partitions ok but you might run out of space fast. Windows free space should be the same as installed size. Say your Windows partition is 100gig but Windows only uses 30 gigs of that 100. So you could resize/shrink Windows down to 60 gig without any problems. Another thing to remember is Ubuntu is able to read your Windows filesystem. So instead of copying things like your music and pictures  from Windows to Ubuntu you can open the Ubuntu media players and point them to the Windows files.

---

### Post by Boelcke on 2008-09-05
Also, I don't know what you've read about sizes.  I always make that separate /home partition (that your link recommended), and I tend to need more space in there than in my root partition.  I've got a mature Dapper box that I've been adding software on for years, and the root folder still isn't much over 3 gigs.  It just doesn't take too much space for Ubuntu -- not as much as your Windows partition.  You could make / as little as 5-6 gigs.

---

### Post by flamingswrd on 2008-09-05
Thanks for the input. I feel more confident at loading Ubuntu as a second OS and with some lucky, it should turn out to be my main one. I figure I can do all my "high tech" things on the windows end, and get to know something less evil.

---

### Post by cybrsaylr on 2008-09-06
You don't need a big partition for Ubuntu. I had 5GB partitions and it ran fine. I have 2 dual boot systems and chose 20GB partitions for Ubuntu and they both run great.

---

