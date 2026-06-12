---
title: "Upgrade from12.04 to 14.04.1 problem during procedure"
date: 2014-08-16
forum: New to Ubuntu
---

### Post by dtlongrifles on 2014-08-16
I decided to upgrade to the latest Ubuntu because I kept getting messages that I had "broken pipes" when I would log on and Firefox seemed to crash constantly, recently Calibre started closing spontaneously, I lost communication with my sound card and sometimes the computer would "time out" and take me to my log in screen and ask for my pass word or it wwould completely restart. I figured instead of trying to fix each issue individually, maybe an upgrade would fix it all at once. Unfortunately right in the middle of the upgrade the computer chose to restart itself. Some new packages had been installed and others had been removed when this happened. Now I am unable to log back on. I get the following message:

Filesystem check or mount failed.
A maintenance shell will now be started.
CONTROL-D will terminate this shell and continue booting
after re-trying filesystems. Any further errors will be ignored
root@my login name-Latitude-D520:~# 
Was it waiting for me to do something? 

I waited for 30 minutes and nothing further happened. I know from what  I've read here that it's not good to go messing around in root if you  don't know what you're doing (and I do not). I tried re-booting several  more times with the same result, then I put in an Ubuntu 12.04 CD so I  could at least boot from it (that's how I got online to post this). I  was afraid that I would have to re-install Ubuntu and lose everything on  my computer (about 3000 books in Calibre that I entered one at a time over several months), but when I went to  re-install 12.04, it asked if I wanted to: 
Install Ubuntu 12.04 LTS  alongside Ubuntu 14.04.1 LTS, so the 14.04.1 is recognised by the  computer so I hope there is a way that I can just continue and complete  the 14.04.1 upgrade, perhaps from that root mode that I get when I try to boot without the 12.04 CD.

I hope somebody can help me with this. By the way, since boot ing from the CD, Firefox has not crashed once and my sound card is working just fine.


[TABLE="class: GS"]
[TR]
[TD="class: ok"]

[/TD]
[TD="class: eV"][/TD]
[/TR]
[/TABLE]

---

### Post by mooreted on 2014-08-16
Before you proceed with trying to upgrade the operating system you need to eliminate hardware failure as the cause of your issues. You need to test the hard drive by doing a surface scan. You need to test the RAM with Memtest86+ for several hours. You need to check the temperature your system is running at to make sure it's not overheating. Open it up and blow out all the dust. Re-seat all the cables and cards including RAM. Upgrading the OS isn't going to help if your hard drive is failing.

I recommend the Ultimate Boot CD:

[http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/)

---

### Post by dtlongrifles on 2014-08-16
Okay, that's good to know. Was that meant as a "You should have done this instead of what you did" or is that an answer or a solution to the current problem? My question was really, is there a way to continue with the upgrade? Since I was in the middle of it and now I can't eve log back in, I want to know if the upgrade can be continued and if it can and someone possesses the knowledge of how to do that, I would appreciate very much and I would be ever so grateful if they would share their knowledge of that procedure with me. I have no idea how to do a surface scan, never heard of this memtest or how to run it. I switched from Windows to Linux becaue I hate microsoft. I'm not an expert with computers, obviously. I use computers and I just want an operating system that will run when I turn the machine on.

---

### Post by Rob Sayer on 2014-08-17
That was an answer.  That many problems all of a sudden does kind of smell like hardware problems.

While it may be theoretically possible to fix the upgrade, it's an advanced topic and I can assure you that you wouldn't like what you saw.

You'd be better off to just do a clean reinstall, after doing some hardware tests as suggested.  I've reinstalled for much less.  It sounds daunting at first but I never do a release upgrade anymore.  I reinstall.  I only did it once or twice and it worked fine for me.  But I've seen so many problems people had upgrading here I won't do it now.

It's hard to say what you're dealing with because the only clue is the "Latitude-D520" in your terminal output.  That indicates an old cpu/gpu that may be having support issues, which show up a lot if you search for ubuntu intel 945g.  That's a common reason for getting open pipe messages at boot.  It's using llvmpipe because it won't run openGL.

Which may or may be true because that may not be your adapter.  You can find that out here:

[http://askubuntu.com/questions/72766/how-do-i-find-out-the-model-of-my-graphics-card](http://askubuntu.com/questions/72766/how-do-i-find-out-the-model-of-my-graphics-card)

Though I wouldn't assume upgrading releases will fix llvmpipe messages.

When you do reinstall, which you'd be silly not to at this point, I highly recommend setting it up with a separate partition for /home.  This is incredibly useful if you reinstall or upgrade because it doesn't affect your data and user settings in /home.  As long as you don't reformat /home when reinstalling of course ...

A separate /home also increases performance, which from what I see you'll need every inch of.

If you want to install 14.04, which you should, just make sure your data is backed up and use the whole disc.

Another thing is, if it really is a dell latitude 520, it's an old machine and I would actually put xubuntu on it.  You do *not* want unity (or cinnamon or anything else that needs 3d acceleration) on a computer that is using llvmpipe, or most any other computers that old.  Unity is designed for modern hardware.  I found it too slow on my 4Gb i3 based laptop which doesn't have gma issues.

---

### Post by KJ55 on 2014-08-17
Very good advice from both who replied.  :)

I would like to add it's very simple to do a fresh install just using the live install DVD or USB memory stick (Installation Type: "Something Else" or in other words manual partitioning).  I replaced Ubuntu 12.04.4 LTS with Ubuntu 14.04.1 LTS this way.  

I followed the guide on this webpage ([https://sites.google.com/site/easylinuxtipsproject/upgrade](https://sites.google.com/site/easylinuxtipsproject/upgrade)) for the most part (followed paragraph 5.2, in particular); but, I disagree with the author of this webpage of not having a separate partition for /home.  I have a separate partition for home at mount point "/home", a separate partition for Ubuntu 14.04.1 LTS at mount point "/".  Also, a separate 1 GB, in size, partition for swap.   

And, I did delete, and then format with Ext4 the partition that contained the Ubuntu 12.04.4 file system.  And, then installed Ubuntu 14.04.1 LTS on this partition.

But first, check out your hardware.  Linux is very good operating system for informing you of hardware problems.  In other words; if your system runs Linux without problems, your hardware is good.

---

### Post by KJ55 on 2014-08-17
I apologize to the OP of this thread.  I just re-read "read" your problem.  Your salvation is probably your live 12.04 boot disk.  Take a look at this webpage ([http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)). I used it in the recent past to create my separate /home partition.  I believe you may be able to save your files by moving them to a separate /home partition.

And you defintely, don't want to allow an automatic install of Ubuntu at this point.  Mess with the data on your partitions (and the partitions themselves) once you feel somewhat comfortable manually doing.  You should become very knowledgeable in using GParted on the 12.04 boot CD.  

It's not rocket science, and google is your friend.  Also, a very Linux knowledgeable friend wouldn't hurt either.  I have been using Linux; since Y2K, and I have never experienced the errors you're getting, nor had a bad (partial) Ubuntu upgrade.  

P.S.  If you have any doubts about the reliability of the computer - get your personal files off that system now...try to save them.  My priorities would be: (1) Copy your files to a USB memory stick to save them after booting with the 12.04 CD, then (2) create separate partition on the hard drive for a separate /home directory and copy your personal files there, as well, and (3) fresh install (replacement install) on Ubuntu 14.04.1.

---

### Post by dtlongrifles on 2014-08-17
It is a Dell Latitude D520. It has 4 MG Ram and a 500 GB hard drive. I opened it up and it looked very clean inside. I blew everything out with canned air, removed the both Rams (the one under the key board and the one that is accessed from the bottom of the computer) and I finally figured out where that memtest is. I ran it and it took all night, with the end result of no errors found. I downloaded Xubuntu 14.04 but in order to make CD to install it, I had to first install an OS but I loaned my Ubuntu 12.04 CD out and never got it back. I did however have a Pinguy 12.04 CD so I installed it. I've burned the Xubuntu CD.

---

