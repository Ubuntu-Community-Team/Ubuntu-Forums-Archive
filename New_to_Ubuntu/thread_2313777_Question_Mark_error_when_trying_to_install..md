---
title: "Question Mark error when trying to install."
date: 2016-02-15
forum: New to Ubuntu
---

### Post by Conor_Gotzens on 2016-02-15
Hello all, switching from windows trying to become an ubuntu user. Im trying to erase my windows partition and completely install ubuntu on a dell dimension 5100. Everytime i go through the installation process i get to the part that asks for my time zone and an error box pops up with question marks and nothing happens. any help is appreciated! please save me!

---

### Post by Bucky Ball on 2016-02-15
Just a shot in the dark, but do you have an ethernet cable plugged in? Is it possible to take a pic of this question mark screen and attach to a post here? (Adv Reply> paperclip icon).

---

### Post by Conor_Gotzens on 2016-02-15
yes i did have an ethernet cable connected but i also tried it with a wireless connection and got the same error

---

### Post by Bucky Ball on 2016-02-15
Can't make out that picture, too small, but don't see a question mark.

Pull out all internet connections, wired and wireless, and try again. What exactly does it say in that message box?

Incidentally, which release are you trying to install?

---

### Post by Conor_Gotzens on 2016-02-15
did that and get the same error. its ubuntu 14.04.3 
here is a link to a picture of what is popping up [http://s1.postimg.org/1plxlljt0/Screenshot.png](http://s1.postimg.org/1plxlljt0/Screenshot.png)

---

### Post by Bucky Ball on 2016-02-16
See the picture now. Never seen that before.

Which language are you choosing in the part before all this? Or is it after? If those options come before, make sure you are selecting the correct keyboard layout (US) and language (English).

Other than that, completely stumped, sorry. Hopefully someone can offer some clues or you can research some. :-k

Another stab in the dark: Do you have free space on the drive to install Ubuntu to? You are not attempting to install Wubi (Ubuntu in Windows) rather than a dual-boot, Win and Ubuntu on separate partitions? Wubi is no longer supported. Don't go there if that's what you're using. :)

---

### Post by Geoffrey_Arndt on 2016-02-16
Two things:

>   What are the specs for that machine - - mainly, how much ram, and video system?

>   IF you haven't read it yet, Ubuntu needs a halfway modern PC . . at least 1 GB ram, but preferably 2.

This machine is so old "perhaps" antiX will install on it.   see:   [http://antix.mepis.org/index.php?title=Main_Page](http://antix.mepis.org/index.php?title=Main_Page)

---

### Post by Conor_Gotzens on 2016-02-16
it has 2gb ram, and there is enough space for the install. i think it has something to do with something called RAID? im not exactly sure what it is but ive seen other people talking about it with the same issue?

---

### Post by Geoffrey_Arndt on 2016-02-16
Raid is "Redundant Array Independent Disks" . . . used for data security so disk failure on one partition or physical drive does not result in data loss/disaster.   I believe it can be software and hardware based, maybe a combo of both if you have several physical disks.

I've read some types of Raid are supported better in Linux than ohters, but, I've never used any kind of raid setup on my machines - - just use the cloud for daily and weekly backup.  Anyway, RAID may not be the problem.   If you only have 1 physical disk, doing a complete overwrite of the former OS "might" also remove Raid, but again, I'm no expert.   (on install, select the "replace Windows" option).

Perhaps update this thread title so forum readers with Raid experience can add their input.

It might help if you can run "gparted" (from live CD/DVD) and attach a link to a detailed snapshot of your disk(s) partition table.

---

### Post by Conor_Gotzens on 2016-02-16
what is gparted, and how can i go about doing this?

---

### Post by Bucky Ball on 2016-02-17
Boot the live session and Try Ubuntu. Open Gparted from apps. Or, if you are running an install, install Gparted from software centre or in a terminal with:

> sudo apt-get install gparted

RAID? I think you might be confusing the issue. Do you have any evidence this is a RAID issue? RAID is not involved unless you have explicitly setup a RAID array manually. Have you? Please confirm to avoid confusion, thanks. 

You've mentioned nothing about installing a RAID array and people thinking you have will create confusion and make it more difficult to solve your issue(s). 

(As you don't know what a RAID array is, I very much doubt it has anything to do with RAID as you would need to know a fair bit about it to set it up in the first place). :)

* DON'T do anything with the thread title unless you are using RAID.

---

### Post by Geoffrey_Arndt on 2016-02-17
Conor,

If you're serious about installing Ubuntu or any Linux "distribution" . . . one thing that makes it easier is an actual demo of how to do it.    Thanks to Youtube, we can do that very well, but there are several hundred (about Linux installs) to choose from.   Here is one of my favorites - - by Joe Collins.   He is easy to understand, the video is paced right (not too fast) and he covers the topic well.   This video is almost an hour long . . . but it's time well spent if you're willing to do what it communicates.

[https://www.youtube.com/watch?v=kL4DG31tgRM&list=PLTXMX1FE5Hj4q0078_U4iP7JnEC8LPQaP&index=23](https://www.youtube.com/watch?v=kL4DG31tgRM&list=PLTXMX1FE5Hj4q0078_U4iP7JnEC8LPQaP&index=23) 

Also, you might want to view a video about gparted and how to use it:  [https://www.youtube.com/watch?v=0czAJwEbtFs](https://www.youtube.com/watch?v=0czAJwEbtFs)

Note gparted is also already on the Ubuntu Live DVD . . . so, disregard that part of the tutorial, but watch the sections on how to use it.

Good Luck!

LINUX PRE_INSTALLED PC's  . . . . takes about 10 minutes to set up (or faster once you've done it at least one time):   [http://linuxpreloaded.com/](http://linuxpreloaded.com/)

---

