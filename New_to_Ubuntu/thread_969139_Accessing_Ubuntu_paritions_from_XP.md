---
title: "Accessing Ubuntu paritions from XP"
date: 2008-11-03
forum: New to Ubuntu
---

### Post by carusoswi on 2008-11-03
I recently reworked my setup, installing from scratch Ubuntu 8.10 and XP in dual boot onto an empty hard drive.  I had done some reading here, and, based on that, decided to allow (on a 160 gb HD) 50 gb to XP, 90 gb to /home as ext3, 15 gb to Ubuntu, and a 3gb swap file.  From what I read, the 90 gb partition should be able to be read-write for both Ubuntu and XP.

However, XP could not read that partition, so I installed ext2ifs_1_11a which I have used before, and should have fixed the problem.

However, when I attempt to access this partition through XP, I get a message stating that the partition isn't formatted (I think xp calls it a drive), and then asking if I want to format it now.

Of course, I do not.

Further reading on the site from which I downloaded ext2ifs gives me instruction on how to detect the problem, and I get a message stating that the inode isn't equal to 128 or something like that.  Further instructions tell me to back up the drive and reformat it with a certain flag, etc.  

I can go back and reread those instructions and try to follow them, but I'm wondering what I did wrong here.  I've used that ext2ifs utility in the past and never had a problem with it.  What have I done differently this time?

I can live without the storage space on the XP side, but really would like to be able to share files between the two os's.

Can anyone offer suggestions?

Thanks.

Caruso

---

### Post by daimaru on 2008-11-03
I use [explore2fs]("http://www.chrysocome.net/")
to access my linux partitions form xp. I never wanted windows to automatically mount my linux partitions on boot or anything so i opted for this tool that lets me access my linux patitions when i want to.

---

### Post by PierreDeKat on 2008-11-03
> **carusoswi said:**
> Can anyone offer suggestions?
Not to be a smartalic, but the fact that Windows has asked you if you want to format your Linux partition should be a big ol' red flag to you.

My suggestion would be to repartition/reinstall: 20 GB Windows, 20 GB Linux /root, 20 GB Linux /home/, 3 GB swap, and a roughly 95 GB NTFS partition that Windows and Linux can share.

That's more or less what I have, minus the /home/ partition, and I have been pleased as punch with it. Windows and Linux can happily share files, and Windows (and its viruses) have very little chance of buggering up anything important in Ubuntu.

---

### Post by seshomaru samma on 2008-11-03
> **PierreDeKat said:**
> 

My suggestion would be to repartition/reinstall: 20 GB Windows, 20 GB Linux /root, 20 GB Linux /home/, 3 GB swap, and a roughly 95 GB NTFS partition that Windows and Linux can share.


thats a good suggestion
just notice that you can't have more than 4 primary partitions so if you follow this advice one partition will have to be logical.Also you can try a big FAT32 partition to share between Linux and windows.

---

### Post by superprash2003 on 2008-11-03
have you tried fsdriver???[http://www.fs-driver.org/](http://www.fs-driver.org/) ntfs would be a better choice so that it would be directly accessible from xp as well as ubuntu

---

### Post by carusoswi on 2008-11-03
I don't consider your remark that of a 'smartalic', but the Windows message is just that, a message - not a flag, either, just a message that tells me somethin' ain't workin' the way I read that it would.

When I set up this drive, I followed advice from this forum - and, to be honest, I did not see anything stating that I would have trouble accessing the big home partition from XP.  Either I missed it or the advice was faulty.

Is there any way to resize that home partition without having to reinstall?  I have reinstall fatigue.  The drive I installed onto had been configured for Linux Mint, then, I wiped it and installed PCBSD (just wanted to see what it looked like - couldn't get far because it doesn't like my ATI video card - blah!

Then, I decided to just go back to XP/Ubuntu.  Getting Windows to prep that drive and install was like pulling teeth.  I used the drive utility to prepare the drive, no go, XP install coughed half way through.  A couple of formats from XP disk also failed, fixmbr didn't work either.  Finally, a booted into XP dos terminal from the repair console and formatted from there - that one worked.  Don't understand why XP doesn't just take your disk and do as it needs to if you give your approval.  That's one thing I can say for Linux/Unix.  Tell them to take the whole disc, and they take it, period.

Anyhow, If it's possible to resize without starting from scratch, that would be great.

Thanks for the replies.

Caruso

> **PierreDeKat said:**
> Not to be a smartalic, but the fact that Windows has asked you if you want to format your Linux partition should be a big ol' red flag to you.

My suggestion would be to repartition/reinstall: 20 GB Windows, 20 GB Linux /root, 20 GB Linux /home/, 3 GB swap, and a roughly 95 GB NTFS partition that Windows and Linux can share.

That's more or less what I have, minus the /home/ partition, and I have been pleased as punch with it. Windows and Linux can happily share files, and Windows (and its viruses) have very little chance of buggering up anything important in Ubuntu.

---

### Post by edwinlin88 on 2008-11-04
On ubuntu installation, was there the option of formatting the drive as NTFS?

---

### Post by carusoswi on 2008-11-04
> **edwinlin88 said:**
> On ubuntu installation, was there the option of formatting the drive as NTFS?

Probably.  I don't remember what I did.
I wonder if it is too late, now.

I suppose I could fire up the partitioner and have a look at it.

I also wonder if I could format that one partition now without damaging the rest of the installation.

I think if there is no destructive way to make that partition readable by XP, I'm just going to live with the situation as is for a while.

I need to take a break from installing.

Caruso

---

### Post by boof1988 on 2008-11-04
> **carusoswi said:**
> Probably.  I don't remember what I did.
I wonder if it is too late, now.

I suppose I could fire up the partitioner and have a look at it.

I also wonder if I could format that one partition now without damaging the rest of the installation.

I think if there is no destructive way to make that partition readable by XP, I'm just going to live with the situation as is for a while.

I need to take a break from installing.

Caruso

I have used a gparted LiveCD to shrink my /home (linux) partition and it seemed to work fine.  Can't remember if I used it to shrink my XP partition or not.  Believe that it should work (it may just take many hours depending on the number and type of operations involved in the 'shrink').

[Here](http://gparted.sourceforge.net/livecd.php) is where I got the gparted .iso file (in case you need it).

[COLOR="Blue"]Edit:  I found the "[features](http://gparted.sourceforge.net/features.php)" page for gparted... It seems that gparted can do these NTFS operations if you have [ntfsprogs](http://www.linux-ntfs.org/doku.php).  Though, now I'm not sure if the liveCD has ntfsprogs included or not?[/COLOR]

---

### Post by carusoswi on 2008-11-05
Thanks to all for the helpful replies.
I am in a location with my computer where I can get wireless, but no wired connection, so, I am going to put this little issue on hold for the time being.  I don't want to risk breaking my system so that the only step to restore it would be a complete reinstall.  Without a wired connection, I doubt I could get back online if I reinstalled at this point.  I need ndiswrapper in order to load the proprietary driver for my wireless adapter, and, I noticed during the current install that this utility does not install initially, but has to be downloaded from the repositories.  If all I have available to me is a wireless connection, then I would be unable to get the 'net up and running if I did another fresh install.

I'll tackle this problem this weekend.

Thanks again.

Caruso

> **boof1988 said:**
> I have used a gparted LiveCD to shrink my /home (linux) partition and it seemed to work fine.  Can't remember if I used it to shrink my XP partition or not.  Believe that it should work (it may just take many hours depending on the number and type of operations involved in the 'shrink').

[Here](http://gparted.sourceforge.net/livecd.php) is where I got the gparted .iso file (in case you need it).

[COLOR="Blue"]Edit:  I found the "[features](http://gparted.sourceforge.net/features.php)" page for gparted... It seems that gparted can do these NTFS operations if you have [ntfsprogs](http://www.linux-ntfs.org/doku.php).  Though, now I'm not sure if the liveCD has ntfsprogs included or not?[/COLOR]

---

### Post by carusoswi on 2008-11-08
Pierre/sheshomaru:

Ok, trying to follow your suggestions on a reinstall.  I figure I don't really have to touch the 50 gb windows partition if I choose - just leave it at 50 GB, set up the other partitions as you recommend, then, reinstall Ubuntu.  A couple of questions:

1) There are two internal drives in my system, the master HD is 160 gb, the slave (where I keep my data) is 360 gb.  Just now, as I attempted to implement your suggestion, the partitioner came up showing only the 360 gb drive (actually, it didn't actually name either drive, but was offering, by default, to partition the drive it showed into two 150+ gb partitions.  I knew that could not be my master drive, so, to be safe, I have removed that drive from the system (by unplugging the data cable).

Why did Ubuntu insist on installing to my slave drive, and why did it not even offer the option for me to install to the master drive?

2) After unplugging the slave drive, a subsequent opening of the partitioner did show the master drive and all the partitions as I currently have them setup.  I thought I might get lucky and just be able to edit that 90 gb partition as NTFS, but that option doesn't appear to be available.  I also thought I might be able to delete all the non-windows partitions, redefine them, and then install Ubuntu again.  However, when redefining the partitions, there seems to be no NTFS format option available to me.  My choices include Fat16, FAT32, EXT2, EXT3, but no NTFS.  Why is this?

3) If I cannot format the large partition as NTFS using the partitioner, perhaps I should just boot into XP, try accessing the large partition, and answer yes when XP offers to format it for me.

I suppose I could also just allow the partitioner to set the partition up as FAT32 or FAT16, then, from XP, convert that partition to NTFS.

Further suggestions would be appreciated.

Thanks.

Caruso

> **PierreDeKat said:**
> Not to be a smartalic, but the fact that Windows has asked you if you want to format your Linux partition should be a big ol' red flag to you.

My suggestion would be to repartition/reinstall: 20 GB Windows, 20 GB Linux /root, 20 GB Linux /home/, 3 GB swap, and a roughly 95 GB NTFS partition that Windows and Linux can share.

That's more or less what I have, minus the /home/ partition, and I have been pleased as punch with it. Windows and Linux can happily share files, and Windows (and its viruses) have very little chance of buggering up anything important in Ubuntu.

---

### Post by ugm6hr on 2008-11-08
> **superprash2003 said:**
> have you tried fsdriver???[http://www.fs-driver.org/](http://www.fs-driver.org/) ntfs would be a better choice so that it would be directly accessible from xp as well as ubuntu

Before you go doing anything drastic - have you tried this?

If Ubuntu is your primary OS it is much easier to use /home as your storage partition (since all apps will default to saving there).

I have used fs-driver for about 2 years with no problems at all.  I would strongly recommend it over an NTFS partition, particularly since Ubuntu will be unable to read it if Windows crashes for some reason.

If you want 100% compatibility with both OS, only fat drives are natively read/write with both.

---

### Post by carusoswi on 2008-11-08
I haven't tried your suggestion, but will probably give it a try.  Here is what I don't quite understand, however.  My slave HD is formatted NTFS, and Ubuntu has no problem whatsoever reading from or writing to that drive - I think I've been doing that since at least as far back as 7.04, probably even earlier.  Intrepid can presently mount and read/write to/from that hard drive.

I'll do a search on fs-driver and see if I can learn a bit more about it.

Thanks for the reply.

Caruso

> **ugm6hr said:**
> Before you go doing anything drastic - have you tried this?

If Ubuntu is your primary OS it is much easier to use /home as your storage partition (since all apps will default to saving there).

I have used fs-driver for about 2 years with no problems at all.  I would strongly recommend it over an NTFS partition, particularly since Ubuntu will be unable to read it if Windows crashes for some reason.

If you want 100% compatibility with both OS, only fat drives are natively read/write with both.

---

### Post by sdowney717 on 2008-11-08
ifs drives works great winth inodes of 128, older ext2 and 3 formats.

the new formats for linux ext3 and up are using inodes of 256 and they dont work.
I emailed them and was told in the next release ifs drives will support inodes of 256.

---

### Post by carusoswi on 2008-11-08
I find that I have fs-driver (or its equivalent) already loaded.  What I decided to do was go ahead and let XP format that large partition to NTFS.  Unfortunately, I had labeled it /home for my Ubuntu 8.10 install, so I broke my Ubuntu system.  Fortunately, I'm not far into setting that OS up (not many installed aps and such), so, I just reinstalled Ubuntu from scratch.  No, I have XP on a 50 gb partition, Ubuntu / on a 17 gb partition, Ubuntu /home on another 17 gb partition, a 3 gb partition as swap, and the rest is a large NTFS partition - similar to the arrangement recommended earlier in the thread.

When I booted back into XP, it initially gave me that dreaded 'not formatted' message, but, I guess I didn't realize that behind the scenes, XP was busy configuring my 'new' hardware.  I received a message that the 'new' hardware was ready but that I needed to restart.  Restarting gave me full access to the empty NTFS partition.

I still have to mount all my internal non-Ubuntu drives/partitions by clicking on them - so I guess they have the wrong inode (per the response further down in this thread).  I still don't quite understand all of that, but it only takes a couple of seconds to go to Places - Computer - and click on each of those 'drives' to mount them after booting up.  Then, I have full access to all storage space on the system.

Funny that the external drives (I have three of them) mount up automatically.

One thing I have always appreciated about Linux-Ubuntu is the relative ease with which you can just scrap your system, reinstall a fresh version, and, even if you don't save all your software and settings, things can be put back to where they were before you reinstalled in almost no time.

Reinstalling XP is truly a pain.  I have to make certain I have all of my critical system disks (mother board driver, graphics card driver, sound card driver) and all my critical software packages handy (with authorization codes, etc.) or a reinstall will leave me high and dry with an OS that is fresh, but virtually incompatible with my system.  Getting USB 2.0 drivers loaded and recognized in XP has always been problematic on my system.  I don't know if I should blame that on MS or Shuttle (I have an XPC small form factor machine).

At any rate, this has been an interesting exercise.  I can live with the system the way it is now . . . time for me to get to work.

Thanks for all the great advice.

Caruso

> **ugm6hr said:**
> Before you go doing anything drastic - have you tried this?

If Ubuntu is your primary OS it is much easier to use /home as your storage partition (since all apps will default to saving there).

I have used fs-driver for about 2 years with no problems at all.  I would strongly recommend it over an NTFS partition, particularly since Ubuntu will be unable to read it if Windows crashes for some reason.

If you want 100% compatibility with both OS, only fat drives are natively read/write with both.

---

### Post by carusoswi on 2008-11-08
. . . one last thing.  How do you invoke that FS-driver from XP to configure it?  My /home, /, and swap partitions show up with drive letters, but are still not accessible.  I'm not so certain I'd need to access any of these from XP, so would like to remove them from the XP list of drives when I click on 'my computer'.

How would I go about doing that?

Caruso

---

### Post by sdowney717 on 2008-11-08
the program is run from control panel
from there you assign drive letters.
If no drive letter assigned, then they dont show up.

there is a utility you can run to check why ifs drives is not loading.

called mountdiag.exe

[http://www.fs-driver.org/troubleshoot.html](http://www.fs-driver.org/troubleshoot.html)

I ran into the problem of inode size. My main ubuntu ext3 partition will mount. But I recently added a second drive and that ext3 partition has an inode size of 256, which is not compatible with ifs drives

ALSO, you cant run an exe file from a ext3 partiton using windows.

---

### Post by carusoswi on 2008-11-08
Inode size was the problem that was described when I ran that check.  I don't understand inode size, or why it prevents auto mounting or why, absent auto mounting, I can simply click on the drives, dismiss the ominous error message, and the drive then functions as normal.  Makes no sense, but it is only a minor inconvenience.

Caruso

> **sdowney717 said:**
> the program is run from control panel
from there you assign drive letters.
If no drive letter assigned, then they dont show up.

there is a utility you can run to check why ifs drives is not loading.

called mountdiag.exe

[http://www.fs-driver.org/troubleshoot.html](http://www.fs-driver.org/troubleshoot.html)

I ran into the problem of inode size. My main ubuntu ext3 partition will mount. But I recently added a second drive and that ext3 partition has an inode size of 256, which is not compatible with ifs drives

ALSO, you cant run an exe file from a ext3 partiton using windows.

---

### Post by ugm6hr on 2008-11-08
> **carusoswi said:**
> Inode size was the problem that was described when I ran that check.  I don't understand inode size, or why it prevents auto mounting or why, absent auto mounting, I can simply click on the drives, dismiss the ominous error message, and the drive then functions as normal.  Makes no sense, but it is only a minor inconvenience.

I'll have to look into this too.  I use my ext3 /home as a storage partition, but I only boot into Windows about twice a year (I have a work logbook that requires my PDA and Access), and I have had no problems with fs-driver so far.  Obviously, I need to kepp it that way!

---

### Post by constantine lotek on 2008-11-09
greetings,

it seems to me that the initial problem in this discussion was how to access files on the ubuntu partition from windows.

i have windows xp and ubunto 8.10. i can't rea-install stuff cause i will go crazy.

from looking online it seems that communication with ntfs(windows format) and ext3 (ubuntu format) is made possible by using one of these programmes that can easily be installed on windows:
1.) [http://ext2fsd.sourceforge.net/](http://ext2fsd.sourceforge.net/)
2.) [http://www.fs-driver.org/](http://www.fs-driver.org/)
3.) [http://www.chrysocome.net/explore2fs](http://www.chrysocome.net/explore2fs)

I have tried all three of these and none have worked. though the first two let me assign drive letters to my ubuntu partitions but when trying to access windows asks me if i want to format the drives, and off course  don't cause that would mean loosing ubuntu and all my files there. 

As already mentioned it is possible to use the 'mountdiag diagnosis tool' if using option 2, but when i tried this not much happened. a window opened and closed very quickly.

It seems to me that the most probable reason is that inodes that are size 256 are not compatible with ifs drives. Though i am not sure what this means. but it could maybe be a problem that exists because of inode size in ubuntu 8.10? The above options seem to have worked for people for years. 

So I've tried the 3 mentioned options, I have a vague theory that I don't understand and I really don't want to install everything again.

Please could someone help me.

Thanks:)

---

