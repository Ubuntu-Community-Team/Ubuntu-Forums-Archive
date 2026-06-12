---
title: "[SOLVED] Dual boot.  Ubuntu first then Windows?"
date: 2008-07-21
forum: New to Ubuntu
---

### Post by mal_conductor on 2008-07-21
Hello,

I am going to install UBANTU right now.

I would like to have a dual-boot (Windows/UBUNTU).

What is the _BEST_ thing to do?  Install UBANTU first then Windows or Windows first then UBANTU?

I don't care if one is more work, but I do care about best results.

I was thought it had to be UBUNTU first because Windows does not let other OS coexist, but now I see the installation CD offers to install "parallel" to Windows.  Again, I am willing to install both from scratch is it yields better results.

Thanks to all

===========================

Thank you all.  I now have Ubuntu running.

My problem was that I did not see the slide-bar (to create a partition) when installing Ubuntu with Windows.

The reason I did not see the partition slide-bar was that Ubuntu thought there were corrupted sector on my hard drive.  Running CHKDSK did not solve the problem.

The solution was to install Windows again.  When installing I deleted all partitions and created one partition for Windows with half hard disk space (The rest of the hard disk remained as unused space).
The when installing Ubuntu I chose to install on the largest available space.

I hope this can be of help to others
Highly recommend this guide [http://www.herman.linuxmaniac.net/p24.html](http://www.herman.linuxmaniac.net/p24.html) (Many thanks to laffinet)
Thank you all for your help.

---

### Post by Rolcol on 2008-07-21
I think it's easiest to install Windows first and then Ubuntu since GRUB (installed when you install Ubuntu) sets up so you can boot into either windows or ubuntu.  By editing the menu.lst file, you can chose which to boot automatically after a timeout.(ubuntu by default)  If you don't want to mess with menu.lst but rather have a GUI to help you, install startupmanager
```
sudo apt-get install startupmanager
```

---

### Post by tuxxy on 2008-07-21
Windows then Ubuntu, also you wont need to partition anything in windows you can do this at Ubuntu installation.

---

### Post by Joeb454 on 2008-07-21
The best thing to do would be to install Windows first and have some free space (unpartitioned) to install Ubuntu in.

If partitioning sounds scary then you could try installing Ubuntu under Windows first (which won't require any partitioning).

It depends how confident you are - partitioning is always a risky business

---

### Post by mal_conductor on 2008-07-21
If I install windows first what/who partitions the hard drive to install UBUNTU?

Will UBUNTU take over some of the space mapped by Windows (Keep in mind that Windows has the entire hard disk mapped)?

Thank you all,
Please be patient

---

### Post by rockstarrem on 2008-07-21
Ubuntu has a GUI guided slider that lets you choose how much space you'd like to give Ubuntu and how much space you'd like to give Windows. It will automatically create the partition for you. Install Windows first then Ubuntu otherwise you'll run into some booting problems that I have no idea how to fix.

---

### Post by jamesrfla on 2008-07-21
When you install Windows it will use the entire disk to install. Then after your done installing windows the Ubuntu will shrink the Windows partition to what ever size you want then Ubuntu will create the partitions for Ubuntu.

---

### Post by Joeb454 on 2008-07-21
I think you may be better off installing Ubuntu under Windows for the time being :)

---

### Post by mal_conductor on 2008-07-22
OK guys,

I installed windows first.  Then Ubuntu.

At step 4 of install Ubuntu asks How I want to partition disk?
1) Guided - Use entire disk
WILL THIS WIPE OUT MY WINDOWS INSTALL?!!!

2) Guided - use the largest continuous free space
It says some partitions are to small.  OS will not work properly

3) Manual
More choices:
a- Edit Partition: (gives a bunch of choices like ntfs, swap area and others)

b- Delete Partition

If I don't do anything and click "Forward" it says "No root file system is defined"

=========

Help

---

### Post by laffinet on 2008-07-22
> **mal_conductor said:**
> OK guys,

I installed windows first.  Then Ubuntu.

At step 4 of install Ubuntu asks How I want to partition disk?
1) Guided - Use entire disk
WILL THIS WIPE OUT MY WINDOWS INSTALL?!!!



Yes it will, so don't use this option. 

There should be a "guided resize" option which is the easiest way to do it. Look here: [http://www.herman.linuxmaniac.net/p24.html]("http://www.herman.linuxmaniac.net/p24.html") for an illustrated guide.(you have to scroll down a bit to get to the right section.

---

### Post by mal_conductor on 2008-07-22
laffinet,

Thanks for helping.

I am using the install CD.
I put in the Ubuntu install CD and booted my PC.
The Ubuntu set-up starts.  It says there are 7 steps.
(Language, Time Zone, Keboard, 4) Partitioning)

Step 4 is where I got stuck.  Where is the "options" you mentioned?

Also, I read other posts where people install from "Live CD" is that better?

---

### Post by laffinet on 2008-07-22
You are using the live CD.

Have you looked at the link I provided? Scroll down to section 012, is this where you're at ?

---

### Post by mal_conductor on 2008-07-22
I am not sure what "live C" is.  I thought it meant running the Ubuntu demo from within windows.

I put my disk in the tray in rebooted my computer.
UBUNTU started installing kind of the same way a windows installation starts.

Ubuntu then walks me through these 7 steps and I am at #4

I was not shown "options" at any point.  Is there another place to make the partitions and then come back to starting the Ubuntu install?

can you help, cheers.

---

### Post by laffinet on 2008-07-22
Alright, I'll be away for about 30min now, but will come back to help you.
In the meantime, have a look at the link I posted and let me know how that compares to what you've done so far.
The options I mentioned are at point 4, you should have an option that says "guided-resize".
Again, please have a look at the link in my first post.

---

### Post by mal_conductor on 2008-07-22
Thank you.  I had missed the link.

I will ready.  Will let you know if I need further help.

Thank you.

---

### Post by mal_conductor on 2008-07-22
laffinet,

This guide is very good.
Yes, I was at screen shot 012.
The guide should take me through the installation.

However,  the system found some bad sectors on my hard drive.  I am running chkdsk, as suggested by the guide, and this is taking a long time.  Again, thank you.  I will post if I need more help.

One more thing.  How do I tag a thread "SOLVED"

many thanks

---

### Post by kdb424 on 2008-07-22
If you have any more questions I am willing to help. Installing Ubuntu on a PC is easy. On a mac, not so much. Aren't you lucky. lol


edit: To tag the thread solved, just edit the first post and change the topic to [SOLVED] Your topic goes here.

edit 2: please don't double post. Use the edit button if no one has posted since you last posted. you are new, so I'm sure you won't get in trouble this time.

---

### Post by laffinet on 2008-07-22
> **mal_conductor said:**
> laffinet,

This guide is very good.
Yes, I was at screen shot 012.
The guide should take me through the installation.

However,  the system found some bad sectors on my hard drive.  I am running chkdsk, as suggested by the guide, and this is taking a long time.  Again, thank you.  I will post if I need more help.

One more thing.  How do I tag a thread "SOLVED"

many thanks

Glad I could help. Let me know if you have any more problems.

To tag a thread solved go to "Thread tools" (above the thread) and select "mark as solved"

---

### Post by kdb424 on 2008-07-22
Laffinet. I didn't know that. lol. I learned something here! Mal, if you still need help, I'll keep checking the topic.

---

### Post by laffinet on 2008-07-22
That's what this forum's for.

If you want to get notified when someone's posting in this thread just subscribe to it with "instant email notification".

---

### Post by kdb424 on 2008-07-22
I think I knew that one, but the others reading this thread might not have. Thanks so much! mal_conductor, you all good and running ubuntu now?

---

