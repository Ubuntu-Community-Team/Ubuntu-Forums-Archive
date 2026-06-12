---
title: "different filesystems on the same disk"
date: 2012-12-10
forum: New to Ubuntu
---

### Post by unibroker on 2012-12-10
I am dual boot Ubuntu 12.04 64 bit/WinXP.  I have been having daily, ongoing startup problems but after a couple of hard shutdowns my computer stabilizes and the rest of the session is uneventful.

I was reading an Ubuntu Documentation on Partitioning/Home/Moving and the last section got my attention ```
Different filesystems on the same disk
If you're moving from Windows and your new home partition is going to be an old ntfs partition (the D: disk) while you convert the C: disk to a journaling partition where you install Linux, this won't work, there will be a huge load on the processor. You should convert the two partitions to ext3 or ext4 or keep both partitions as ntfs (I haven't checked this last option). But working with two different filesystems on the same drive simultaneously doesn't seem to be a good option.
```

I currently have both ntfs and ext4 on my hard drive and the same setup on my external drive.  My processor is working extra hard the first several minutes of a session as shown by System Monitor.  Am I reading this right that my existing hard drive setup is not recommended?  Does this mean that the drive should only contain ntfs as long as I have WinXP in dual boot?

---

### Post by oldfred on 2012-12-10
Your quoted statement does not make sense??

Linux only runs on Linux formatted partitions not Windows formatted partitions except for wubi.

I notice a slight increase in boot time or about 5 sec when I add the mounting of a NTFS data partition, but never see any slow down otherwise.  I have my processor in a icon in my top panel so I can see what is happening.

You should never hard shutdown system if it can be avoided. You often have to run chkdsk on Windows and fsck on Linux as file systems then need repairs. Best to remember the elephants.

       Holding down Alt and SysRq (which is the Print Screen key) while slowly typing REISUB
R-E-I-S-U-B to force shutdown
A good way to remember it is.
Raising Skinny Elephants Is Utterly Boring ...or
Reboot System Even If Ultimately Broken ...LOL.
[http://kember.net/articles/reisub-the-gentle-linux-restart/](http://kember.net/articles/reisub-the-gentle-linux-restart/)

---

### Post by Herman on 2012-12-10
I don't know where they got that idea from, who ever wrote that about not having more than one file system in the same disk. 
As far as I know we can have as many different partitions as we want, with as many different file systems as we like and it wouldn't matter one iota whether they are in the same disk or in different disks.
It takes a few seconds longer at boot time for the computer to spin up extra hard disks, and then for the operating system to mount all the extra file systems.

Perhaps you should try running some file system checks to make sure all of your file systems are healthy. Use Windows own tools for your NTFS and use GParted from a Live CD to run a file system check in your Ubuntu partitions (when they are not mounted). It may help or maybe not make any difference, but a file system check is a good thing to do every once in a while.

EDIT: And as oldfred says, learn ways to avoid hard shut downs, they are not good for your file systems. :)

---

### Post by unibroker on 2012-12-10
> **oldfred said:**
> 

       Holding down Alt and SysRq (which is the Print Screen key) while slowly typing REISUB
R-E-I-S-U-B to force shutdown
A good way to remember it is.
Raising Skinny Elephants Is Utterly Boring ...or
Reboot System Even If Ultimately Broken ...LOL.
[http://kember.net/articles/reisub-the-gentle-linux-restart/](http://kember.net/articles/reisub-the-gentle-linux-restart/)

I never have seen that method or any others for that matter.  I'll have to look for one that is geared to a single hand.  I tried positioning that one several times and the distance between Alt and Print Screen keeps me from being effective.  Thanks for the headsup just the same.

I must haven't done much damage because both filesystem checks on the hard drive and external hard drive were completed in 30" time.

---

### Post by Jmackxxx on 2012-12-10
I think he got the quote form windows which we all know does not detect Linux/other File system.....
You can have up to 7 total partitions/logical partitions  with whatever file system

---

### Post by oldfred on 2012-12-10
The limits with MBR partitioning are 4 primary partitions, one primary can be an extended and virtually unlimited number of logicals in the extended.

With gpt partitioning the standard limit is 128 but there may  be work arounds to have more.

One user did test the number of logicals and he put 100's but each was 2 or 3 sectors per or not really useful, but it was allowed.

---

### Post by unibroker on 2012-12-11
I tried your method of shutdown this morning and it failed because when I get these daily startup crashes the mouse and keyboard are frozen.

---

### Post by oldfred on 2012-12-11
I then start to think you may have hard ware issues.

Have you run memory tests? Sometimes just cleaning & reseating memory helps. But it could be just about anything.

---

### Post by unibroker on 2012-12-11
> **oldfred said:**
> I then start to think you may have hard ware issues.

Have you run memory tests? Sometimes just cleaning & reseating memory helps. But it could be just about anything.

When I select both Memory Tests from grub i get ```
error: too small lower memory 0 x 99100 > 0 x 96c00
```

This has got to have something to do with all of the startup crashes I get every morning with I turn the computer on.

---

### Post by oldfred on 2012-12-11
How much RAM do you have and can you remove one module? Some systems want two matched, most will run with one.

If so, you can test with one RAM memory module and then with the other to see if  it makes a difference.

---

### Post by unibroker on 2012-12-11
> **oldfred said:**
> How much RAM do you have and can you remove one module? Some systems want two matched, most will run with one.

If so, you can test with one RAM memory module and then with the other to see if  it makes a difference.

I have 2, 1G sticks.  I will try your suggestion when I have more time and report back here.  

Thanks for your input.

---

### Post by unibroker on 2012-12-11
I believe the system is detecting both memory sticks. I have System Monitor running and under Memory and Swap History it tells me how much of 2GB I am using so I would guess it's detecting both sticks.

---

### Post by audiomick on 2012-12-11
> **unibroker said:**
> I believe the system is detecting both memory sticks. 

Yes, but if the memtest is turning up some kind of error, you want to find out where it is.

You can usually isolate a RAM problem to one stick by taking out one, running memtest, swapping the one RAM stick for the other and running memtest again.

Given that it is unlikely that both sticks have developed problems at the same time, it is likely that memtest will only show errors with one of the two sticks.

Then, you try booting with only the stick installed that shows no errors. Memtest should show zero errors if the RAM is good.

You should be able to run the machine on only one stick of RAM until you can organise a replacement (or an upgrade to more RAM...).

---

### Post by unibroker on 2012-12-12
> **oldfred said:**
> How much RAM do you have and can you remove one module? Some systems want two matched, most will run with one.

If so, you can test with one RAM memory module and then with the other to see if  it makes a difference.

I ran the computer with each stick removed and got the same error message as when they were both in place.  The sticks are occupying banks 0 and 2. The computer ran fine with only one stick in place at a time.

---

### Post by oldfred on 2012-12-12
That seems like RAM is ok. But then something else must be. Not sure if hardware or some software.

---

### Post by unibroker on 2012-12-12
Looks like this bios error message was being associated with ASUS motherboards which is what I have.  [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=549429]("http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=549429")

---

### Post by unibroker on 2012-12-13
I wanted to post 2 interesting links that I found while researching this memtest error.  The error message seems attributable to larger rams.  The first link proposes a patch and a modification to your bootloader.  [http://bitcube.co.uk/content/memtest-failures-0]("http://bitcube.co.uk/content/memtest-failures-0")

The second is from a Debian bug report started in 2005 and progressing to the patch in 2009.  I found it interesting but over my head; good lesson though.  [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=319837]("http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=319837")

---

### Post by unibroker on 2012-12-15
> **oldfred said:**
> I then start to think you may have hard ware issues.

Have you run memory tests? Sometimes just cleaning & reseating memory helps. But it could be just about anything.

I wanted to give you an update.  I was using gparted this morning and noticed a "memtest86    v4.2" as one of the options on the initial screen.  I ran it and the tests (I did 2 passes) ran with no errors.

Also, since your recommendation of physically removing the memory sticks and booting the computer with 1 of the 2 in place each time, I have had no freezes/lockups on initial boot!  Seems like your suggestion has re-seated the sticks and cured what has ailed my system for months.  Thank you for that.

---

