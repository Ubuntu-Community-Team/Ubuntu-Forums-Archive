---
title: "grub rescue"
date: 2012-05-29
forum: New to Ubuntu
---

### Post by Cube89 on 2012-05-29
hi everyone,
i have a problem that i hope can be fixed.
ill start from the very start.
my computer started acting up few weeks back. so i decided to save all my files on an external hard drive. so i moved to a new flat and got my computers all setup and that when i turned on my computer an error came up with missing operating system. sorry should of said i was running vista at the time lol.also vista wasnt able to read one of my hard drives. so i tried to repair it but failed. so i updated to windows 7 still didn't work so i decided to use Ubuntu. so i thought i could maybe use a vm of vista or have it alongside with Ubuntu.  so i installed Ubuntu with no problems until i restarted it. it came up with an error 
[CENTER]
"not such a file dc826d06-rf96-4565-9fce-95fa8e118bd4"


grub rescue> 
[/CENTER]

please help

thanks 
Cube89

---

### Post by wilee-nilee on 2012-05-29
From the link get the boot-repair tool, run the boot info summary and post the HTTP address, I would not run any thing else yet, but that, the script is for finding problems.

You can run the tool from a live Ubuntu cd or download its cd.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by deadflowr on 2012-05-29
This sounds like a failing disk.
So lets get this straight,
1)first it starts acting strange, you did the right thing by backing up your files.
2)you moved, when you turned on the system for the first time after you're move it said no OS.
3)repair failed
4)upgrade to win7 failed
5)ubuntu installed but does not boot.
That file line you posted is the UUID(univerisally unique identifier) of your disk/partition.

First off, follow wilee- nilee's post's link, and suggestion.
Second, while in the live Ubuntu cd, open up a program called disk utility. On the left hand side is a pane with along the media devices listed(Cdroms, sdcards, hard drives etc) locate your hard drive(it will probably say somenumberGB) if it is there click on it and look at the information to the right, if lucky it can read the smart data and will tell you if the disk is healthy or not.
If no hard drive is found that might mean the connections are loose, if so you'll need to get into it to resecure any loose connection.

---

### Post by jonhosseini on 2012-06-04
forgive the out of place post... but i cannot find any other place to get an answer... i am a completely new member and very new to linux.... can someone tell me how to initiate a new thread, a simple post on the forum with my problem... for the life of me i cannot find anywere on the menus that show anything like "start new thread" or "write post"... please help

---

### Post by drs305 on 2012-06-04
> **jonhosseini said:**
> forgive the out of place post... but i cannot find any other place to get an answer... i am a completely new member and very new to linux.... can someone tell me how to initiate a new thread, a simple post on the forum with my problem... for the life of me i cannot find anywere on the menus that show anything like "start new thread" or "write post"... please help

jonhosseini,

Welcome to the Ubuntu Forums!  :-)

Click on this link to take you to the [_Absolute Beginners Forum_]("http://ubuntuforums.org/forumdisplay.php?f=326")

At the top left, you will see a "New Thread" button.


@ Cube89,

I also recommend Boot Repair. There is a link in my signature line.

---

### Post by jonhosseini on 2012-06-04
> **drs305 said:**
> jonhosseini,

Welcome to the Ubuntu Forums!  :-)

Click on this link to take you to the [_Absolute Beginners Forum_]("http://ubuntuforums.org/forumdisplay.php?f=326")

At the top left, you will see a "New Thread" button.


@ Cube89,

I also recommend Boot Repair. There is a link in my signature line.

thank you cube89 ... i'm on my way...could i ask that you look at my problem that i posted in the thread that your boot repair link directed me to.

---

### Post by YannBuntu on 2012-06-04
**@jonhosseini:** please group all your comments in your specific thread: [http://ubuntuforums.org/showthread.php?t=1996531](http://ubuntuforums.org/showthread.php?t=1996531)

---

