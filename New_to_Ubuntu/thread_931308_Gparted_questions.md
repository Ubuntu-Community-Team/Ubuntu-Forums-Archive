---
title: "Gparted questions"
date: 2008-09-27
forum: New to Ubuntu
---

### Post by carusoswi on 2008-09-27
So, I'd like to create a new primary partition on my hard drive (or one of them).  Right now, sda1 is ntfs, has 40 gb unused and the mount point is /media/sda1, sda2 is ext3, has 5 gb free, and its mount point is /.

 I'm showing an sda3 that has 2.33 gb, file system is 'extended', no used/unused info given, just ---- in both columns.

Under sda3 (on the same tree) is another extended partition labeled swap, it's 2.33 gb, and also there is no info given about free or unused space.

I have another internal disc, and two large usb external discs (one 500 gb, one 750 gb.

The main drive above is 150 gb - it's my C drive in XP, and, obviously, my main drive in Ubuntu, although I admit to not knowing that much about how Ubuntu is supposed to be set up on my hard drive.

Anyhow, when I bring up GParted from the Ubuntu menu, the above information is presented.

I read that one should boot from a Gparted CD to actually change partitions because a disc has to be unmounted to make changes.

Just for the heck of it, I unmounted that main drive described above, and the yellow and white indications for used/unused spaced all turned to gray, so, whether or not one should use the desktop version of Gparted to resize, that option isn't going to work for me.  If I don't unmount, most of the gparted menu choices (including resizing) are greyed out.

So, I booted into a gparted CD.  My main HD still came up as one ntfs partition and none of its space was reported as used (the box is all gray, no yellow/white areas.

If I select one of the other drives, the used/unused info appears to be there.

So, what is it that I am doing wrong?

I'd really like to throw on another distro just for fun, but I really don't feel like breaking down my system and having to reinstall XP/Ubuntu/whatever.

I've done some browsing, but cannot find the sort of simple step by step instructions that I need . . . well, I've found them, and they seem simple, but, when I try to use the program, I'm not seeing what those instructions lead me to believe I should (yellow/white, black resize arrows, etc.).

Advice would be much appreciated.

Thanks.

Caruso.

---

### Post by louieb on 2008-09-27
> So, I booted into a gparted CD. My main HD still came up as one ntfs partition and none of its space was reported as used (the box is all gray, no yellow/white areas.GParted will do that if it thinks the partition is "dirty".  Make sure you shutdown windows (do not hibernate). If that fails then boot windows in safe mode and run chkdisk. That should clean it up. 

> I'm showing an sda3 that has 2.33 gb, file system is 'extended', no used/unused info given, just ---- in both columns.

Under sda3 (on the same tree) is another [COLOR=DarkOrange]extended[/COLOR] partition labeled swap, it's 2.33 gb, and also there is no info given about free or unused space.That's the normal way the Debian / Ubiquity installer will setup your swap partition. (virtual memory in widows terms).   BTW that partition is a [COLOR=DarkOrange]logical[/COLOR] partition. 

> the sort of simple step by step instructions that I need . . . well, I've found them, and they seem simple, Nice description of what going on. Sure you'll get it figured out. You may want to make sure you understand the 3 partition types primary, extended and logical.  GParted  is pretty simple (well maybe not at first).
[Linux.com Gparted videos]("http://www.linux.com/articles/114157") 
Good Luck.

---

### Post by carusoswi on 2008-09-27
Thanks for your reply.  I really don't understand the difference between primary and extended partitions.
Just so you know, my system currently is dual boot, XP and Ubuntu 8.04.  I felt like messing around with something different this morning, but don't want to break my system.

Just to be certain, I have pulled my master drive out of the system and installed another 150 gb drive in its place to which I will install some other test OS's.

But, if I find something I'd like to keep, I'll still need to figure out how to add a partition without wrecking my system.

Just about every time I've reinstalled Ubuntu, I manage to mess up the drive and have to start from scratch.

I need to get better at that part.

When I browse and read about GParted, it seems simple.  Just doesn't seem to work out that way on my system.

BTW, I wasn't booting from XP or starting Gparted from XP.  I tried to look at my system from the desktop version from within Ubunut, then, shut the computer down and booted with my gparted disc in the optical drive.

Thanks again for your comments.  I'm doing this for fun and instruction, so no frustration here, but I would like to better master this partitioning thing.

Partition magic from within Windows used to seem pretty simple to me, and I'm guessing gparted should be equally so, I just am not getting at the moment.

Caruso

> **louieb said:**
> GParted will do that if it thinks the partition is "dirty".  Make sure you shutdown windows (do not hibernate). If that fails then boot windows in safe mode and run chkdisk. That should clean it up. 

That's the normal way the Debian / Ubiquity installer will setup your swap partition. (virtual memory in widows terms).   BTW that partition is a [COLOR=DarkOrange]logical[/COLOR] partition. 

Nice description of what going on. Sure you'll get it figured out. You may want to make sure you understand the 3 partition types primary, extended and logical.  GParted  is pretty simple (well maybe not at first).
[Linux.com Gparted videos]("http://www.linux.com/articles/114157") 
Good Luck.

---

### Post by Kellemora on 2008-09-27
Hi Car

I hope I don't get SHOT DEAD for saying this!

The gparted on the Ubuntu disk is lousy, probably and older version.
Download the gparted iso from the web and burn a gparted only CD.....

I had NONE of the problems I encountered previously using the new stand alone gparted disk.  It looked and worked the same, the point being it WORKED for me, whereas the Ubuntu distribution wouldn't work right.

Said I had 8 bad blocks, then 119, then 149, chkdisk never found a single bad block or sector.  I reran it and rebooted until I darn near wore out the Drives, and myself hi hi.........

The stand alone gparted did the trick and everything was humming along just fine after that.

In the end I still wiped XP from the machine entirely to make room for more STUFF!

I too use older hard drives to experiment with things on!

TTUL
Gary

---

### Post by louieb on 2008-09-27
> **Kellemora said:**
> Hi Car

I hope I don't get SHOT DEAD for saying this!

The gparted on the Ubuntu disk is lousy, probably and older version.

:KSBang your dead.  (right) I use the [SystemRescueCd]("http://www.sysresccd.org/Main_Page")  
The Ubuntu live CD has GParted 3.5 while not a bad version the latest version of GParted is 3.9.

---

### Post by Elfy on 2008-09-27
I use partedmagic which hasn't caused me any problems either - I think I had an odd gparted version at somepoint.

---

### Post by carusoswi on 2008-09-28
Well, I've spent most of the weekend experimenting with some new OS's.  The power and data cable that connects my master HD are sufficiently long (and my handy-dandy small form factor XPC Shuttle is compact enough) that I can pull off the CPU case cover and just set one of my spare HD's on top of the exposed DVD/CD drive, disconnect the power and data cables from the master HD and plug them into this spare drive and experiment away.  I downloaded Linux Mint, and was able to load my proprietary Belkin N1 wireless driver and ATI graphics card driver and everything (not to my sruprise) worked very simlarly to Ubuntu.  Figuring out how to get to the software repositories to find the stuff that I use was more challenging, however.  What I really wanted to play with was wine, but could not find exactly what I need.

Personally, while I know I would get used to that interface, I found it left me luke warm.  For me, I see no real advantage over plain old Ubuntu.

I also downloaded and installed PC BSD 7.  Everything went well, except that it chokes on my graphics card and gives me a black, blank screen.  I can unplug my video cable, remove the card, and plug into the port for my onboard video (which is very lame), and I can get to the main PC BSD screen.

Again, however, without knowing how to load my wireless driver, I have no internet (and I'm not convenient to a wired connection.

So, that was a time consuming bust.

Looks like that OS isn't that much more crisp than Ubuntu, however, although I didn't really give it a workout.

Still have both on CD's.

So, anyhow, I haven't played much with partitioning this weekend, but I did download each of the parition utilies you all mentioned above.  I'm going to practice with them on my spare drive until I am comfortable enough to attempt changes to my working drive.  I just really don't want to have to wipe that drive clean and start from scratch.  My Ubuntu ain't perfect, and XP is XP, but they are working and I have many applications loaded, up, and running.  It would take, probably, another weekend for me to get all that stuff loaded up and working again, and I just don't have the energy for that right now.

Thanks again for the replies.

Caruso

---

