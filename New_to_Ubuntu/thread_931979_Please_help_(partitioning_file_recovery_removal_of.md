---
title: "Please help (partitioning? file recovery? removal of windows?)"
date: 2008-09-27
forum: New to Ubuntu
---

### Post by Arsin on 2008-09-27
So I believe this is the correct place to ask this question.

I recently installed ubuntu to run alongside windows, i choose between the two on boot up. The reason i did this is so i didn't lose all my windows files (i.e. pictures movies) so i found out how to get to those files while on ubuntu and copy/cut them into my ubuntu places. This worked well and fine until it said i did not have enough space in my places to put my windows files. So at first i thought that that partition ubuntu had created for itself (or at least i thought it did) was too small, wrong, there is still only one partition on my whole c drive NTFS. So i want to know how i can get more space to finish putting my documents into my places so i can eventually uninstall windows and run only ubuntu. Please put this in the simplest of forms for me, im familiar with terminal, but i only know how to cut and paste codes into it.


Sincerely 
First Post
Arsin

---

### Post by Bruce M. on 2008-09-27
You say you only have drive C - NTFS. How did you install Ubuntu?

---

### Post by Arsin on 2008-09-27
When i put the cd in i just chose to install it with windows.

---

### Post by Victormd on 2008-09-27
Did you install using Wubi?

---

### Post by alzie on 2008-09-27
This looks like a Wubi install.

What I'd recommend is to save those important files (like pictures) that are hard/impossible to replace to DVDs or CDs.

You might consider an external hard drive as well or a virtual hard drive on the web.

Whichever way works for you having a backup copy is the best way to go.

---

### Post by Arsin on 2008-09-27
So this wubi install please explain more? I have an external with some of it on there but its dedicated 99% to music. But your suggesting saving all my Personal windows pictures and what nots to a external then removing windows?

---

### Post by Victormd on 2008-09-27
> **Arsin said:**
> So i want to know how i can get more space to finish putting my documents into my places so i can eventually uninstall windows and run only ubuntu. Please put this in the simplest of forms for me, im familiar with terminal, but i only know how to cut and paste codes into it.

It seems like you installed Ubuntu using Wubi. Before properly answering your question:
1. How big is your HD?
2. Are you using Vista or XP (this is important for partitioning purposes)?
3. Aside from your files, is there anything else (i.e., specific programs that only run in windows) that would require you to have windows? Or in other words, would you be ready to move to ubuntu now?

---

### Post by Arsin on 2008-09-27
my hd is approx 237gigs 
im running XP (i believe its sp2)
Other than my pictures and videos theres nothing i don't mind losing, any programs i probably pirated and will get later most likely. (i.e. adobe cs3 corporate edition)


btw i love your sig the part about binary my brother didn't get that but i did then he laughed at me. :( lol

---

### Post by alzie on 2008-09-27
A Wubi install is an Ubuntu install from inside of Windows.  You do not have to actually make disk space or format because Wubi runs on a Virtual Disk.  It is similar to a live CD in this way but it does allow you to save files inside a directory on your hard drive, so the files are inside of your Windows Directory.

You can find the Wubi Guide here:  [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

Since you are considering moving to an Ubuntu only computer.  I would strongly suggest that you back up everything of importance.  If this is a Wubi install if Windows gets corrupted then you could very well lose all your Ubuntu files as well.

---

### Post by Arsin on 2008-09-27
ok that makes sense so when i want to switch over fully to ubuntu ill have to reinstall ubuntu but this time different?

---

### Post by Victormd on 2008-09-27
> **Arsin said:**
> my hd is approx 237gigs 
im running XP (i believe its sp2)
Other than my pictures and videos theres nothing i don't mind losing, any programs i probably pirated and will get later most likely. (i.e. adobe cs3 corporate edition)

The reason I asked all this, is because most likely you won't be able to run your windows progs under ubuntu (even through Wine - check [http://appdb.winehq.org/](http://appdb.winehq.org/) I don't think photoshop CS3 is all that great under wine...)

Also, if you intend to transition completely to ubuntu, or if you would like to keep windows (in case you need a windows-specific program or grames), I would suggest dual-booting by actually creating and installing ubuntu on a separate partition rather than using the Wubi install. This way, when your ready to take the jump, all you have to do is delete your windows partition and nothing will happen to ubuntu. The way you have it set up now, you need windows to run ubuntu (as Alzie posted, it's an ubuntu install inside windows)...

Guess I'm just trying to get a feel for where you want to go so we don't give you any wrong advice or the wrong idea... :)

> **Arsin said:**
> btw i love your sig the part about binary my brother didn't get that but i did then he laughed at me. :( lol

Thanks! :) hehehehe... not many people get it...

---

### Post by alzie on 2008-09-27
Is this the installer that you used?

[IMG]https://wiki.ubuntu.com/WubiGuide?action=AttachFile&do=get&target=wubi-123.png[/IMG]

Sorry about the big pic.  It is of the Wubi installer program.

There is a method for making a Wubi install into a regular install here: [http://ubuntuforums.org/showthread.php?t=438591](http://ubuntuforums.org/showthread.php?t=438591)

Seriously, I wouldn't consider changing until all important files are backed up.

---

### Post by Arsin on 2008-09-27
Adobe is really the only thing that i use thats windows specific and im sure i can figure a way to run it in linux even if its under WINE or maybe use GIMP. games and what not i have done the research and there is enough there for me to work with. basically im so fed up with windows and always wanted linux im finally ready to make the switch i just want my pictures and personal stuff

---

### Post by Arsin on 2008-09-27
yeppers thats what i used. so i just back up mah junk and im good to switch???

---

### Post by Victormd on 2008-09-27
> **Arsin said:**
> yeppers thats what i used. so i just back up mah junk and im good to switch???

IF you're sure that you're ready to switch, backup all your data (DVD, CD, external HD, etc...) put in the live CD and format your HD to install ubuntu! :D

---

### Post by alzie on 2008-09-27
Pretty much.  I tried to do a Wubi to normal conversion.

I ended up reinstalling Windows and dual booting because I messed things up so badly.  Now you know why I rant about backups  :lolflag:

Good luck

---

### Post by Boelcke on 2008-09-27
I made the jump, and went without Windows for nearly 2 years.  I'm back now to a mix of machines (1 XP, 2 ubuntu), but I'd have to say this:

With disk space being cheap, why be in a rush to ax your Windows partition?  Run ubuntu, use it full time, but what's 30 gb to keep Windows, just in case you need it once or twice?  It's no sin. BTW, how big is the HD, and how much free space do you have left?  I would:

backup the data

Partition the drive so Windows is smallish (30 gb?)
Maybe put the pictures & music on a shared partition (fat32 so they both could read it)
Or, make a /home partition with enough space on it for all your data
put ubuntu root on a small parition (5-10 gb)

It doesn't hurt you to keep windows, unless you're that tight on disk space.  Even then, if you take pictures and get music like I do, you're going to run out soon anyway!

---

### Post by RU-In? on 2008-09-27
May I suggest...

That if you have already put in a lot of time getting your Ubuntu install the way you want it, eg: backgrounds, themes, personal files, etc., then also make a copy of your Ubuntu /home directory too. One of the neat things about Ubuntu (& Linux in general), is that you can copy everything in your home directory (in a simple/straight forward way) and restore it in a new installation and all of your files and settings (at least most settings) will be there again. Even if you set preferences in software, and the software is not installed (on the new setup), when you re-install the software your preferences will be there again. This is because most of those files are hidden files in your home directory. They begin with a '.' (dot). 

**Quick and Dirty way to do this:**
When you are in your home directory, just press ctrl-h, and your hidden files will show up. This method is so straight forward, that if you just simply copy and paste the contents (after showing hidden files), and just press 'skip' when it complains...you will have most of the files copied. Most, meaning that it will complain about a few, but it will get the bulk of whats important. This method has been quite effective for me in the past, not perfect but effective. :)

The only other thing to keep in mind is to 'deselect' the ones you won't need, like the 'examples' link. Also easy, when all of the files are selected, hold down the ctrl key and click the ones you don't want. Another folder that comes to mind is '.thumbnails', you wont need this one either, but no biggy if you take it.

This is quick and dirty, but it will save a lot of setup time on the next install. Once you have re-installed, just copy and paste them back into your new home directory, don't forget to 'unhide' the files on your backup before selecting for copying back to the new home.

There are also scripts and 'one liners' (for the command line) that will do a more thorough job too, but at least this method will save a little time and get you close to where you where. In the future, you can use better methods to make periodic backups of your home directory. When you have your system the way you really like it, you will want to use a better, more refined, method. For now, this is a simple way to kind of pick up where you left off, so to speak. 

Also, if you already installed a lot of software packages, and you have the external hard drive space (or CD/DVD), you can copy your apt-cache directory (if apt was set to not clear cache right away), and recopy it too into the new setup, and you will save a lot of time downloading all of those packages when you re-install. Those are located in the directory:

```
/var/cache/apt/archives
```

(I don't know why I wrapped the above w/ 'code' tags, it just seemed right) 

Just take a look and see if there is a lot of content, and again, just put them back in the new system...this will require 'root' privileges when copying back into the new setup, but that will also give them the right settings when restored.

Well, hope this is actually helpful and not to pedantic :) 

Good Luck...

---

