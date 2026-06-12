---
title: "(A MUST READ!!!!!) The Ultimately Fastest Ubuntu Desktop/Server You Can Have!"
date: 2006-08-30
forum: Outdated Tutorials &amp; Tips
---

### Post by axely on 2006-08-30
O.k.  You have read the title and I am here to tell you that I have found something out about Ubuntu and Linux in general after 1 month of scientific/practical research and implementation.

1-- EXT3 is the absolute slowest part of Ubuntu.
2-- XFS is the fastest file system. Period.  This is uncontestable.
3-- Preload and Prelink do help when using EXT3, but very much so when using XFS.

I hope this thread will help the many of you that thought Ubuntu was slow and sluggish.  It is in EXT3 but not XFS.

Here are my findings---

1. Formatting 500GB in ext3 takes around 10-15 mins. Formatting the same drive in XFS takes (no kidding) 7 seconds (if you don't believe me try it).

2. Network traffic was slow.  My network is setup perfect (as it is what I do for a living) and I could not achieve any greater than 5Mb/s no matter what I did in ext3, and it would eventually simmer down to around 2-3 after around 1 hour of transfer.  XFS....no less than 11.1Mb/s at all times, no matter what I am doing, and no degregation of signal at all. (10/100 switch).   

3. Packet loss.  After monitoring 20 250GB transfers from one machine to the next, I achieved a 13-15% rate of packet loss using ext3.  Absolutely none with XFS and the tranfer took 1/8 of the time (no kidding).

4. Using vmware-server like I do everyday for everything, including real world projects/servers, I wondered why it was so slow.  The problem...ext3.  I installed vmware-server on XFS and the machines are at least, and I mean at the very least, twice as fast for boot and operations.

5. I was wondering why no matter how I niced my transfer process I could gain no more speed than if the transfer (ftp, ssh, smb, etc) would not go any faster or use anymore cpu.  The answer.  XFS.  It took full advantage of the multithreading capability of my cpu (as it uses raw i/o access) and my cpu (amd 32bit/64) is now being used correctly, whether for transfer or normal i/o operations (copy, create, delete, etc.)

6. Multitasking.  I can honestly say, I am on a complete different level with XFS.  It will make use of your processor and filesystem like you never thought possible.  Nothing seems to slow down no my Seagate 7200 rpm 250Gb sata (8mb cache).  It is like new I tell you.

7. Gaming. Again, not even close with ext3.  XFS makes doom3 and anything else run at least 75-100% better.

8. XFS gave me 6 gig back on my harddrive (98.02% usage).

9.  Stability.  Well, I hate to say it, but XFS is more stable than ext3.  I did approximately 15 cold shutdowns while in the middle of processing for both filesystems.  Had to do 3 checks with ext3.  Zero with XFS

10. Swap.  Let's just say now, with XFS it actually does feel like I have 4 GB of RAM.  Swap slowdown, seems to have dissapeared.

11. Multimedia editing (something I do everyday with video and audio).  Simply put, if you do either, make the switch to XFS.  It's a totally different experience.

I conducted all of these tests by using fresh install of both filesystems, including reiserfs, at least 20 times over the last month.  I read over 30 articles relating to both filesystems and comparisons to JFS,REISERFS,etc.  And yes, I tweaked out ext3 everytime with indexing, writeback, noatime, etc.  Still, no comparison, at all.  I can also say this with confidence.  Try to transfer 200Gb of data over a network with ext3 and you will lose something in the transfer.  That was 20/20 times.  XFS, again, 0% loss of any kind.  

You can ignore this thread, but you would be doing yourself a great diservice.  XFS is the only "real" next generation filesystem and the only one I will use from now on. Just when I was going to leave Ubuntu after buying new switches and switching cables, (8 times) for another distro because of the sluggishness, technology found me.  Your hardware is fine.  Switch filesystem and you will see the light, and if networking is your job or passion, or is just a necessity to have working at full speed.  XFS is a 100% sure bet to achieve maximum throughput on your LAN.

My partitioning scheme is as follows.

desktop

100MB /BOOT --ext3
2GB SWAP
250 / --xfs
----------------------------------------
For my 2 raids I use the following
server1

100MB /BOOT --ext3 (raid 1 partition)
4GB SWAP (raid0 partition)
800MB / -- xfs (raid0 partition)

all same disks x2

---------------------------------------
server2

100MB /BOOT --ext3 (raid 1 partion)
8GB SWAP (raid0 partition)
1.25TB / -- xfs (raid1 parition) (20 second format)

all same disks x2
-----------------------------------------
[B][COLOR="Red"]Use prelink and preload from this thread --
[http://ubuntuforums.org/showthread.php?t=74197](http://ubuntuforums.org/showthread.php?t=74197)
Along with the above partitioning scheme, and you will be in Linux heaven[/COLOR].[/B]

Some articles:

[COLOR="Green"]http://en.wikipedia.org/wiki/XFS
[http://linux-xfs.sgi.com/projects/xfs/papers/xfs_white/xfs_white_paper.html](http://linux-xfs.sgi.com/projects/xfs/papers/xfs_white/xfs_white_paper.html)
[http://www.soe.ucsc.edu/~sbrandt/290S/xfs.pdf#search=%22xfs%20scale%22](http://www.soe.ucsc.edu/~sbrandt/290S/xfs.pdf#search=%22xfs%20scale%22)[/COLOR]

tools:

Use gkrellm or iptraf to measure your lan speed.  
apt-get install iptraf gkrellm

This is my contribution to Ubuntu, for helping to create a business I couldn't have had without it.  Hats off to all of you here at the forum and everyone else who has helped me get here.  Thanks!

Axely

(P.S)
I am writing this article on my Ubuntu desktop while transfering 93 GB worth of vmware files to my renewed server with the scp processed niced to level 19....transferring (according to gkrellm) at 12.5MB/s on my 10/100 lan (that has never seen that speed since Ubuntu's implementation)......all without a hitch.  Machine is 2 years old, 2GB RAM, AMD 1.8.  Simply a joy to use now....

Enjoy!

---

### Post by Antonlacon on 2006-08-30
Xfs is good for larger files, but...

If you don't have a reliable power source, meaning UPS, loss of power can hose the system.

#7 will need an explanation.  Unless your hard drive is thrashing during a level, filesystem has very little to do with anything besides load times.

#9 can be deceiving as the writes sitting in cache may not have been written and you may have zero'd files of the proper size or older versions. This also reflects on #10.

#4,8,11 have to do with xfs's superiority with large files.

Xfs is nice, but not perfect.

(side note, bonnie++ ([http://www.textuality.com/bonnie/](http://www.textuality.com/bonnie/)) will let you benchmark I/O.)

---

### Post by ss0007 on 2006-08-30
so , how do i convert my existing ext3 to XFS ?

---

### Post by csy on 2006-08-30
while this sounds a bit exagerated id be willing to give this a try

---

### Post by Ramaddan on 2006-08-30
Hi,

Nice info.

1- Is it possible to convert current filesystem without losing
data and settings? If yes, how?

2- Are there any compatibility issues, or drawbacks?

3- If XFS is good, why wasn't it used by default when installing Ubuntu?

Thanks for the info.

---

### Post by foxy123 on 2006-08-30
why not JFS then? it shows even better performance according to the tests...

---

### Post by Rui Pais on 2006-08-30
> **Ramaddan said:**
> If XFS is good, why wasn't it used by default when installing Ubuntu?

XFS behaves badly with power loss or bad shutdowns. 
There is plenty known cases where after abrupt power down or problems at shutdown the system had they files replaced by zero sizes files or files with same size but only with zeros on it!! As far as i read no recover possible (except using a backup).

And although fast, specially with large files, axely is exaggerate a little...

---

### Post by bluenova on 2006-08-30
Certainly sounds good. I would like to hear from some more people who have switched to XFS, and I'd also like to know why ext3 is the default. Is it just because of
> If you don't have a reliable power source, meaning UPS, loss of power can hose the system.

And is there any change for the end-user, i.e file permissions/ownership etc, or do they all work in the same way?

---

### Post by frodon on 2006-08-30
> **bluenova said:**
> Certainly sounds good. I would like to hear from some more people who have switched to XFS, and I'd also like to know why ext3 is the default. ext3 is the default because it's the most reliable FS.

XFS is good but if you want to try another FS don't forget reiserFS which is also faster than ext3 but obviously less reliable.

---

### Post by Paulo Wageck on 2006-08-30
i have been using reiserfs.... very stable and nice..
try it out.

---

### Post by peachy on 2006-08-30
> **ss0007 said:**
> so , how do i convert my existing ext3 to XFS ?
You could try this:
[http://gentoo-wiki.com/HOWTO_Convert_Filesystems]("http://gentoo-wiki.com/HOWTO_Convert_Filesystems")

Although I've never tried it so can't guarantee it won't screw your FS

---

### Post by bluenova on 2006-08-30
> **Paulo Wageck said:**
> i have been using reiserfs.... very stable and nice..
try it out.
Do you notice a big speed difference compared to ext3?

---

### Post by foxy123 on 2006-08-30
I used to use reiserfs on Breezy. However, Breezy itself was slower than Dapper so it's different to say if the file system was faster or not. I had reiserfs on SuSE some time ago (I guess it's default there, though I may be wrong) and had some unpleasant experience when though i have not lost my data but had to reinstall the system as the file system became corrupt after some crash and did not want to cure :)

---

### Post by bluenova on 2006-08-30
Thanks for your input foxy123. From what you are saying perhaps it's best to do this:

/ reiserFS or XFS
/home ext3
/swap reiserFS or XFS

Does anyone know the differnces between reiserFS and XFS, as in speed, reliability?

---

### Post by Rui Pais on 2006-08-30
[Here]("http://linuxgazette.net/122/piszcz.html") are some famous benchmarks between filesystems.

ReiserFS is usually faster then ext3, specially for small files, but have a know problem of quickly (and badly) fragments, degradating performance very fast.

Another problem (small one) in XFS is more cpu consumer then ext3.

JFS is usually not much used or referred since most people find it, in opposition to ext3, to much new and very little experimented  (and reiser4 too in fact).

---

### Post by mejy on 2006-08-30
While I am aware of the performance boost from using XFS (I use it myself), I can't help feeling that some of your claims are... exaggerated.

"1. Formatting 500GB in ext3 takes around 10-15 mins. Formatting the same drive in XFS takes (no kidding) 7 seconds (if you don't believe me try it)."

This is because there is more than one way to format any file system - there's a quick format that just wipes the index so that all space is treated as free space, and then there's a thorough one that actually gos through and zeroes each bit on the disk.

"2. Network traffic was slow. My network is setup perfect (as it is what I do for a living) and I could not achieve any greater than 5Mb/s no matter what I did in ext3, and it would eventually simmer down to around 2-3 after around 1 hour of transfer. XFS....no less than 11.1Mb/s at all times, no matter what I am doing, and no degregation of signal at all. (10/100 switch)."

11.1Mb is about 1.2 megabytes per second, and to be frank any file system can handle that easily, unless you have a drive spinning at 1000 RPM.  On pretty much any network file transfer, the network connection is the bottle neck (the exception being the 1Gb/s connections that are still rarely supported).

3". Packet loss. After monitoring 20 250GB transfers from one machine to the next, I achieved a 13-15% rate of packet loss using ext3. Absolutely none with XFS and the tranfer took 1/8 of the time (no kidding)."

Again, this sounds very like a network issue.  Unless the ext3 file system is very corrupted (which is possible), then packet loss will be through the network connection.  An eight times file transfer increase is simply not possible through just changing file systems.  Period.

"4. Using vmware-server like I do everyday for everything, including real world projects/servers, I wondered why it was so slow. The problem...ext3. I installed vmware-server on XFS and the machines are at least, and I mean at the very least, twice as fast for boot and operations."

This is certainly possible on a machine with little RAM, but the actual raw processing/graphical speed would obviously be uneffected.  Twice as fast to boot sounds surprising, but is possible on low ram/slow hard disk computers.

"5. I was wondering why no matter how I niced my transfer process I could gain no more speed than if the transfer (ftp, ssh, smb, etc) would not go any faster or use anymore cpu. The answer. XFS. It took full advantage of the multithreading capability of my cpu (as it uses raw i/o access) and my cpu (amd 32bit/64) is now being used correctly, whether for transfer or normal i/o operations (copy, create, delete, etc.)"

"Again, unless this is very high bandwidth network connection, the file system is not the bottle neck and is not responsible for the speed increase.  I/O operations on a local machine WILL be faster, but you'll only notice if you're doing it with either very many or very large files."

"6. Multitasking. I can honestly say, I am on a complete different level with XFS. It will make use of your processor and filesystem like you never thought possible. Nothing seems to slow down no my Seagate 7200 rpm 250Gb sata (8mb cache). It is like new I tell you."

This depends on your configuration - if you have a slow CPU and fast hard drive, you won't want the processor being used for file operations.  This is a farely vague point, so I'll leave it at that.

"7. Gaming. Again, not even close with ext3. XFS makes doom3 and anything else run at least 75-100% better"

This point is simploy not possible.  Although levels may load quicker, Doom 3 doesn't access the hard disk at all during normal game play.  Unless you have very little RAM and it's improving swapping speed (and still, not by 100%), file system will not effect the actual FPS in game.

"8. XFS gave me 6 gig back on my harddrive (98.02% usage)."

Sounds extreme, but if you have millions of smallish files on a large hard drive, I suppose it's possible.

"9. Stability. Well, I hate to say it, but XFS is more stable than ext3. I did approximately 15 cold shutdowns while in the middle of processing for both filesystems. Had to do 3 checks with ext3. Zero with XFS."

This is because ext3 is very conservitive when it comes to checking (it will check often when there isn't any corruption), and XFS often doesn't check even when the file system is corrupted.  Also, the most recent data will not be present after a reboot due to caching and many files that were in use may be zeroed or extremely corrupted.  File system checks/crash is not a measure of file system stability.

"10. Swap. Let's just say now, with XFS it actually does feel like I have 4 GB of RAM. Swap slowdown, seems to have dissapeared."

Depending on your amount of RAM, you may see a significant increase.  With 1.5-2 GB I can think of few instances where you'll be swapping intensively.  Also, the actual bandwidth of the IDE/SATA connection is about 1/100th of that of actual RAM, so this is exaggerated at the very least.  Swap is no substitute for RAM, no matter what the FS.

"11. Multimedia editing (something I do everyday with video and audio). Simply put, if you do either, make the switch to XFS. It's a totally different experience."

There would certainly be an increase in video editing, but in audio editing the files are not large enough to see the hard disk slowing it down much.  On any file system, a 50GB wav takes a few seconds to read.  This may be down to swap I suppose, but again this sounds exaggerated.

Pre-loading could well see a performance boost since it involves reading large aomounts of data from the disk as quickly as possible.

I'm happy you've found a file system that works for you, but don't try to get others to switch based on false or exaggerated information.  It sounds like you atleast used a different network connection with each file system, and many of your other claims seem exaggerated and are without benchmarks.

---

### Post by axely on 2006-08-30
Noted reply......

I don't think I said you "have to switch"  Noone in the forums says you have to do anything.  Since every system is different, what I listed was straight from experience.  On my system, it seems like a G*d send.  So before you tell me what not to do...check yourself buddy.  Noone is telling anyone else to do anything.  If you don't like it, don't read it, but don't discourage others from trying.  What it did for me, was in a word, much needed.  Even thought it might be because I deal with 10 GB video files everyday from my file server.  Either way it worked.  If everyone kept there mouth shut and only spoke if they had concrete graphical/statistical data to support everything said here in the forums, it would be a lot smaller and a lot less exciting.  Again, check yourself bro, and do whatever you want.  Noone is pulling your leg.  To others, I say, give it a whirl, you might find what I found.  By the way, I have had no data loss after over 20 forced power downs.  Maybe just luck, but we'll see!:D 

Axely

---

### Post by codejunkie on 2006-08-30
i use jfs it's just as fast as xfs with most day to day tasks, and is more reliable than xfs or reiserfs, it seems to handle hard reboots and power outages with no damage to the filesystem like you get sometimes with reiser and xfs for me it just works. as for ext3 it can be slow and it seems like the longer you use the system the slower it gets, but you can speed it up a great deal by adding the [**elevator=cfq**]("http://ubuntuforums.org/showthread.php?t=119546&highlight=elevator%3Dcfq") option to the kernel.

---

### Post by MetalMusicAddict on 2006-08-30
> **axely said:**
> Noted reply......

I don't think I said you "have to switch"  Noone in the forums says you have to do anything.  Since every system is different, what I listed was straight from experience.  On my system, it seems like a G*d send.  So before you tell me what not to do...check yourself buddy.  Noone is telling anyone else to do anything.  If you don't like it, don't read it, but don't discourage others from trying.  What it did for me, was in a word, much needed.  Even thought it might be because I deal with 10 GB video files everyday from my file server.  Either way it worked.  If everyone kept there mouth shut and only spoke if they had concrete graphical/statistical data to support everything said here in the forums, it would be a lot smaller and a lot less exciting.  Again, check yourself bro, and do whatever you want.  Noone is pulling your leg.  To others, I say, give it a whirl, you might find what I found.  By the way, I have had no data loss after over 20 forced power downs.  Maybe just luck, but we'll see!:D 

Axely

I dont feel that mejy's words were any more discouraging then your post was encouraging. It was simply a different opinion.

Also if you title is a recommendation to use this FS on a server I would ask you this; Do you have a server? I honestly wouldnt want to risk my almost 2TB worth of data on mine to a FS thats not solid.

---

### Post by axely on 2006-08-31
On that note....agreed.  So now that I've calmed the he** down from your first post, let me say..

Yes I do have a server...4 to be exact (only 2 over 500GB though)

I'm only using it because I can't get it to crash like people say, even after  15 (now 23) power downs forced on it.  Anyway,  I would like to know what you think of JFS vs. XFS, or something, instead of just telling me it sucks/telling me what not to do.  If you can offer something of that nature, then cool...if not, I'd end the reply about here with me.  Just saying something is bad, without any support whatsoever is what is really misleading.  Moreso than my original post.  Dig up some data...or....well I'll finish that later depending on your reply, if you give one.

Lates......

---

### Post by gatewayasteroid on 2006-08-31
> **axely said:**
> O.k.  You have read the title and I am here to tell you that I have found something out about Ubuntu and Linux in general after 1 month of scientific/practical research and implementation.

1-- EXT3 is the absolute slowest part of Ubuntu.
2-- XFS is the fastest file system. Period.  This is uncontestable.
3-- Preload and Prelink do help when using EXT3, but very much so when using XFS.

I've always used Reiserfs 3.6, fast and reliable.

If Slackware uses it, there must be a reason! 8-)

---

### Post by ygarl on 2006-08-31
> **Rui Pais said:**
> [Here]("http://linuxgazette.net/122/piszcz.html") are some famous benchmarks between filesystems.

ReiserFS is usually faster then ext3, specially for small files, but have a know problem of quickly (and badly) fragments, degradating performance very fast.

Another problem (small one) in XFS is more cpu consumer then ext3.

JFS is usually not much used or referred since most people find it, in opposition to ext3, to much new and very little experimented  (and reiser4 too in fact).


Going through all this (and it's slightly out-of-date now, admittedly...) shows that jfs is the fastest, technically. But ReiserFS looks more stable if somewhat slower. ext3 is the most stable, but slow as a slow thing overall.

I'd put my Edgy partion on jfs, and I already run my ReiserFS partition with Dapper.
Don't know how slow ext3 would be I've never used Dapper on ext3...

Ta,

---

### Post by hugmenot on 2006-08-31
> If everyone kept there mouth shut and only spoke if they had concrete graphical/statistical data to support everything said here in the forums, it would be a lot smaller and a lot less exciting.
I see. Next thing you know someone comes along and claims XFS without a doubt improves his audio and video quality.
Either provide dependable data or don&#8217;t bother.

---

### Post by kerry_s on 2006-08-31
I'm using XFS now, it's not that much faster than reiserfs, I do notice the faster load times for large files like /bin will load alot quicker than reiserfs. I just think it's a matter of choice and what you use your system for, also if you use older linux(DSL,...) some don't have XFS support so you'll be cut off from your files. I've tried the hard power down with things running and i had no problems wth loss, she just started right up. I noticed it runs 3 daemons all the time that logs,checks data, i'm not sure what the last on does, i think it's a buffer(xfslogd,xfsdatad,xfsbufd). Also i see in top that there are 4 zombies, i don't get that with reiserfs. I only just installed so i know it's not something malicious. I've had no problems so far so only time will tell.

---

### Post by bluenova on 2006-08-31
This was a good read:
[http://www.debian-administration.org/articles/388](http://www.debian-administration.org/articles/388)

---

### Post by axely on 2006-08-31
Hey Hugmenot.....

For trying to tell me what to do...kiss my a##.  See if you can dig up some stats on that.  Tired of people like yourself thinking your someone because of a forum.  Let people be and quit trying to be a tyrant.  We can take this conversation to private messaging if you want.  No problem there.  Got some things I'd like to tell you just between, so the forums stay clean.  So I'll meet you there kitten.......

---

### Post by K.Mandla on 2006-09-01
> **axely said:**
> Hey Hugmenot.....

For trying to tell me what to do...kiss my a##.  See if you can dig up some stats on that.  Tired of people like yourself thinking your someone because of a forum.  Let people be and quit trying to be a tyrant.  We can take this conversation to private messaging if you want.  No problem there.  Got some things I'd like to tell you just between, so the forums stay clean.  So I'll meet you there kitten.......
Well, that devolved rather quickly. 

Thanks for the note on XFS. I've tried it, but I'm sticking with ext3 because I work with older machines and I feel the lower CPU strain makes up for the slower structure.

[quote=bluenova]This was a good read:
[http://www.debian-administration.org/articles/388](http://www.debian-administration.org/articles/388)[/quote]
Thanks for that. That's the kind of hard numbers and direct explanation a lot of people look for. Cheers!

---

### Post by frodon on 2006-09-01
Please remember [the forum policy]("http://ubuntuforums.org/index.php?page=policy") and that it is expected that all users of these forums will conduct themselves with politeness and respect...even when you are frustrated. 
I'll not do anything for the moment to give a chance to this thread and by respect to all the users who have posted useful informations and contributed to this thread.
Further posts which break the [the forum policy]("http://ubuntuforums.org/index.php?page=policy") will be move to the jail and infraction points will be issued.

---

### Post by linuxpenguin on 2006-09-01
I used to have a file server that used ReiserFS.  It was an old 200MHz machine with 128MB RAM, a 2.0GB main HD (split with 1.5GB for the OS and .5GB for swap) and a 20.0GB shared drive for the network, a 10/100 Ethernet card, and a barebones Slackware install with only Samba and Webmin.

It wasn't the fastest thing, of course, but transfer rates stayed around 1.5-1.7MB/s (in terms of Mb/s this is about 12-14Mb/s) which certainly isn't fast but is a lot faster than I expected from such an old machine, and it's still great for small files.

---

### Post by Thund3rstruck on 2006-09-07
> so , how do i convert my existing ext3 to XFS ?

From what I unserstand this is not an easy task the way it is in windows to go from FAT32 to NTFS. Apparantly you need to create a new partition with the FS you desire and then migrate the data over. This can be done quickly with a LiveCD.

---

### Post by K.Mandla on 2006-09-07
After axely's endorsement of xfs, I decided to try it out on [this machine]("http://www.ubuntuforums.org/showthread.php?t=246260"), with a setup similar to what you see near the end of that post. Root and home were switched to xfs, with an ext2 boot partition and standard swap; the system was built from a server installation and without a desktop manager.

Boot and load times were similar to ext3 with dir_index enabled, but lagged by a second or two. I blame that again on the file system load being shifted to the processor, when (as I understand it) ext3 is less cumbersome. :neutral: 

Either way, xfs was a far cry from standard ext3, and required far less tweaking to set up than ext3 with dir_index, journal writeback and noatime. Just for fun, I used it on an Xubuntu dual boot on a dual 2.8Ghz Xeon machine with an Ultra SCSI setup. It's alarmingly faster than Dapper's default ext3.

So thanks to axely for pointing this out. Cheers, friends! \\:D/

---

### Post by Rui Pais on 2006-09-08
> **K.Mandla said:**
> 
Either way, xfs was a far cry from standard ext3, and required far less tweaking to set up than ext3 with dir_index, journal writeback and noatime.

Hi,
here a nice [thread]("http://forums.gentoo.org/viewtopic-t-488215.html") (on Gentoo forum) about tweaks on XFS. Some of them are suppose to softer the down sides of XFS.

Just for completeness, for those wondering about the mentioned ext3 tweaks, [here]("http://forums.gentoo.org/viewtopic-t-305871.html") is another excellent thread on how-to do it.

Maybe some of you find it useful :)

---

### Post by jonny on 2006-09-08
I don't recommend XFS on a laptop unless your power management is rock solid.  I have a dodgy battery so accidental shutdowns are common, and in 3 months XFS has twice hosed *all* my desktop settings (panels, recent documents, Epiphany and LifeRea bookmarks) after an abrupt power down.  I'd never previously had a problem with Ext3, although I twice had to use a live CD to rescue file system damage.

My laptop feels (no benchmarks) perceptibly faster with XFS, but my data losses have wasted much more time than XFS has saved me.  I imagine it's perfectly reliable for desktop use, though.

---

### Post by K.Mandla on 2006-09-08
> **Rui Pais said:**
> here a nice [thread]("http://forums.gentoo.org/viewtopic-t-488215.html") (on Gentoo forum) about tweaks on XFS. Some of them are suppose to softer the down sides of XFS.

Just for completeness, for those wondering about the mentioned ext3 tweaks, [here]("http://forums.gentoo.org/viewtopic-t-305871.html") is another excellent thread on how-to do it.
Doh! :oops: I should have linked to those things after having mentioned them. :???: Thanks.

---

### Post by Rui Pais on 2006-09-08
No problem, i use both codergeek and jsosic tweaks either on Gentoo as in Ubuntu and it had already cross my mind to mention it... cause i think they are very useful. 
I just take your references as an escuse to do it ;)

---

### Post by mike3k on 2006-09-08
I'd like to see ZFS. I don't know how the speed is since I've never used it, but I like the features like pool storage (nicer than current RAID implementations), compression, etc.

---

### Post by detectiveinspekta on 2006-09-09
My HDD are almost fill to the max, so I think its impossible to convert to XFS without other hardware.

---

### Post by BoHu on 2006-09-10
I have had good results with both JFS and XFS. Both are faster than reiserfs on the two machines that I run...

desktop 1 = 999mhz with 256 mb ram
desktop 2 = 400mhz with 256 mb ram

the undeserved popularity of reiserfs is something I will never understand.

---

### Post by axely on 2006-09-19
Anytime bro!

---

### Post by Cynical on 2006-09-19
JFS is just as fast as XFS and imho its better at error recovery. Only a week ago my brothers computer (running suse 10.2 on an xfs partition) powered off unexpectedly. When he powered it back up he found that he had lost everything. 

One cool thing about XFS is how hard it is to recover a file after its been deleted. (for those tin foil hat users out there)

Oh and I agree with the Bohu, I went from reiserfs to jfs and my boot time decreased by 10 seconds. Not to mention the added responsiveness to my desktop. I want to try reiser4 soon and see how it compares.

---

### Post by ba5e on 2006-09-19
Use ReiserFS its the best combination of performance and rock solid reliability! :)

---

### Post by ba5e on 2006-09-19
This guy posting this post must work in marketing......

---

### Post by foxy123 on 2006-09-19
> **bluenova said:**
> This was a good read:
[http://www.debian-administration.org/articles/388](http://www.debian-administration.org/articles/388)

after reading all the comments to the article from the link above it seems neither FS has overall any considerable. Some maybe faster, but less reliable, some quicker with files but longer to boot and so on. I guess if you are running a server 24/7 wih UPS, XFC may be a good choice, while on the laptop it may be not.

Anyway, I would firstly try to tweak ext3 before jumping another FS. ReiserFS may be an alternative for me. JFS looks nice but it seems that very few people take it seriously.

---

### Post by halogen on 2006-09-20
I did about 3 months work on tests of different linux file systems for a new batch of servers we were installing as we had a crash and the ext3 file system hosed the fstab file badly. (mangled it with a few other files). 

It came down to XFS and JFS as the performance winners but XFS was even worse than ext3 for power failures hence we decided on JFS. 

Two very important notes with JFS, though, is that it's incredibly slow for deleting large amounts of small files and it doesn't have (as far as I can tell) quota support. 

So we now run the new servers using JFS as the primary file system and manage quotas via software we've built.

---

### Post by Bnonn on 2006-09-20
I don't mean to sound harsh, and I am personally no fan of ext3 and would always show it less favor than XFS, but the OP is simply rubbish.

> **axely]
1-- EXT3 is the absolute slowest part of Ubuntu.
2-- XFS is the fastest file system. Period. This is uncontestable.
3-- Preload and Prelink do help when using EXT3, but very much so when using XFS.[/quote]
1-- define "part", and in what context! This is simply a meaningless statement without some kind of explication.

2-- no, XFS is *not* the fastest filesystem. It is extremely contestable what the fastest filesystem *is*, and XFS is certainly very fast, but there is no clearly-definable "fastest filesystem". For example, XFS is faster than JFS when deleting large numbers of files (something mentioned earlier), but much slower than ext3. However, when finding large numbers of files it's twice as slow as either JFS or ext3. It's about the same speed as ext3 at copying files between disks, and faster than JFS, but then when creating a large file JFS is three times faster than ext3 and significantly faster than XFS, which is still twice as fast as ext3. Additionally, JFS tends to generate about 15% less CPU overhead than XFS. For more information, refer to [this set of benchmarks on Linux Gazette](http://linuxgazette.net/102/piszcz.html), or [this closer-to-realworld set at Debian Administration](http://www.debian-administration.org/articles/388).

3-- I have no problem with this statement, although given the extreme claims that the OP makes, benchmarks to quantitatively demonstrate the speed differential would have been handy.

I will continue to quote items which are either suspect, require quantitative validation rather than qualitative and subjective hype, or are simply wildly outrageous---

> 1. Formatting 500GB in ext3 takes around 10-15 mins. Formatting the same drive in XFS takes (no kidding) 7 seconds (if you don't believe me try it).
If the same type of format is being performed, this seems unlikely. Formating an ext3 partition *does* take significantly more time (minutes rather than seconds), but such a large difference suggests that something more is going on. Formatting a 160 GB drive in JFS takes me no more than 3 seconds, however I don't know precisely what the format process does as opposed to XFS's one, or ext3's one. Anyway, the time taken to format is once-off, and doesn't necessarily tell us anything about the actual speed of the filesytem.

> 2. Network traffic was slow. My network is setup perfect (as it is what I do for a living) and I could not achieve any greater than 5Mb/s no matter what I did in ext3, and it would eventually simmer down to around 2-3 after around 1 hour of transfer. XFS....no less than 11.1Mb/s at all times, no matter what I am doing, and no degregation of signal at all. (10/100 switch).
This falls under the wildly outrageous category. The Linux Gazette article I linked above shows that ext3 and XFS are neck-and-neck when performing copies from the current disk to another, and that even where XFS significantly outperforms ext3 copying from another disk to the current one, ext3 is still pulling almost 30 MBps (note capital B for bytes, not lowercase b for bits). According to the article the testing drive was a Western Digital 250GB ATA/100 8MB CACHE 7200RPM, and the other drive was a Maxtor 61.4GB ATA/66 2MB CACHE 5400RPM. These were both running in a Dell Optiplex GX1, which I know from experience is *not* a fast computer said:**
> 3. Packet loss. After monitoring 20 250GB transfers from one machine to the next, I achieved a 13-15% rate of packet loss using ext3. Absolutely none with XFS and the tranfer took 1/8 of the time (no kidding).
Again, as above. Packet loss does not occur on the filesystem; if there was 13-15% packet loss reading or writing data there would be *widespread* corruption and you almost certainly couldn't boot the disk. However, the fact that ext3 is significantly better than XFS at maintaining data integrity does suggest that, in light of the previously-mentioned slow network speed, perhaps something, somewhere, is causing IO issues. It's possible that there is something going on which is causing significant overhead to ext3 (which tries to work around it), while it's not degrading XFS (because XFS simply ignores it, or something else is preventing it being affected). If this is the case, then it could be a recommendation for ext3 more than for XFS. Anyway, regardless of the problem, network packet loss occurs at the network interface; not the hard disk interface.

> 4. Using vmware-server like I do everyday for everything, including real world projects/servers, I wondered why it was so slow. The problem...ext3. I installed vmware-server on XFS and the machines are at least, and I mean at the very least, twice as fast for boot and operations.
There is a consistent trend here of *significant* underperformance when using ext3, and what seems to be quite typical performance when using XFS. Again, my guess is that something is happening in the background which is degrading ext3 performance due to how ext3 handles data integrity, while not affecting XFS.

> 5. I was wondering why no matter how I niced my transfer process I could gain no more speed than if the transfer (ftp, ssh, smb, etc) would not go any faster or use anymore cpu. The answer. XFS. It took full advantage of the multithreading capability of my cpu (as it uses raw i/o access) and my cpu (amd 32bit/64) is now being used correctly, whether for transfer or normal i/o operations (copy, create, delete, etc.)
Perhaps this is true. Again, though, a more conservative CPU overhead is certainly no recommendation in many instance, despite the OP making it sound like ext3 is doing something wrong.

> 6. Multitasking. I can honestly say, I am on a complete different level with XFS. It will make use of your processor and filesystem like you never thought possible. Nothing seems to slow down no my Seagate 7200 rpm 250Gb sata (8mb cache). It is like new I tell you.
Given that I've seen ext3 and other filesystems running on similarly specced machines exactly as the OP seems to be running in XFS, I am again led to the conclusion that something is wrong with his setup which is causing ext3 performance to degrade, while XFS is simply running as *normal*. On a properly configured and similarly specced system I would be extremely skeptical that anyone could guess what filesystem Ubuntu was using simply by interacting with the desktop and working in different applications. The difference in speed is just not that significant.

> 7. Gaming. Again, not even close with ext3. XFS makes doom3 and anything else run at least 75-100% better.
Again we have a completely non-filesystem-related performance issue cropping up. Since Doom3 is only using the memory subsystem and GPU when playing, the fact that it is so much slower when running ext3 points to the same diagnosis as I suggested for the network issue: something is causing a significant IO bottleneck. If it *is* ext3 then this is clearly an abberation specific to the OP's system. Perhaps he could file a bug report.

> 8. XFS gave me 6 gig back on my harddrive (98.02% usage).
More context is required to make any use of this statement. The current usage of the hard disk, the number of files, their average size, etc, all contribute to the available measured space. Various filesystems pack files in various ways. Quite possibly as the hard disk fills up, XFS will use up progressively more space than ext3 would. However, I concede that XFS is better at allocating space than ext3 is.

> 9. Stability. Well, I hate to say it, but XFS is more stable than ext3. I did approximately 15 cold shutdowns while in the middle of processing for both filesystems. Had to do 3 checks with ext3. Zero with XFS
This indicates nothing except that ext3 has more conservative fsck settings, while XFS is frankly reckless. There are a wealth of benchmarks and articles available online which will prove quite conclusively that ext3 is far better at maintaining data integrity than XFS is; indeed, XFS is generally kept off production machines for the exact reason that filesystem corruption is common when using it. Judging stability by fsck settings merely belies significant ignorance on the part of the OP, and throws serious doubt over *all* his findings.

> 10. Swap. Let's just say now, with XFS it actually does feel like I have 4 GB of RAM. Swap slowdown, seems to have dissapeared.
Again, this points to an IO problem in ext3. Since the difference between the 2 GB of RAM that the OP uses, and the 4 GB he claims to feel like he has, is entirely indistinguishable for normal desktop use, this is not even subjective opinion; it's merely nonsense. Again, the OP displays ignorance both of the difference that hardware will make to the user environment, and of the way in which that hardware works. His implication that having 2 GB of swap and 2 GB of RAM should make the computer "feel" like it has 4 GB of RAM is simply absurd, since RAM not only has a hugely larger bandwidth than a hard disk, but also a hugely lower seek latency (orders of magnitute lower; nanoseconds instead of microseconds). If all availble RAM is being used, then swapping will take place, and it *will* be slow regardless of what filesystem is being used. If all available RAM is not being used, then the filesystem doesn't come into play because swapping isn't taking place at all.

> 11. Multimedia editing (something I do everyday with video and audio). Simply put, if you do either, make the switch to XFS. It's a totally different experience.
At this point, I think it's fair to acknowledge that *for the OP* it's a totally different experience. For anyone else not suffering the apparent IO problems that the OP is, the change to XFS will have a very marginal impact, and one which probably won't even be noticed.

> XFS is the only "real" next generation filesystem and the only one I will use from now on.
This is just absurd. If the OP wishes to validate this claim, I welcome him to try. Until then, I would maintain that ZFS is the only "real" next generation filesystem, and that all the others have some catching up to do. I can at least support this claim by pointing to useful, next-generation features that ZFS offers, which no other filesystems do.

> Your hardware is fine.
Very likely; unfortunately, I would hazard a guess that the OP's isn't. *Something* is causing that IO bottleneck...

On a personal aside, I recently converted my 160 GB storage drive from ReiserFS to JFS. After doing this, my boot time was reduced from 52 seconds to 30 seconds, because there is no longer a zombie reiserfs.fsck process waiting around for 22 seconds while booting. This does not mean that other people will have the same experience (though I have seen some mention on this thread about slow boot times with Reiser). It also doesn't mean that Reiser is a worse filesystem if a 22 second longer boot process is not *critical* to you. Many people will swear by Reiser. For anyone reading this thread, I would strongly advise that you research the issues involved with filesystems carefully before deciding to switch (unless you have no data that you care about), and take the OP with a *large* grain of salt.

Regards,
Bnonn

---

### Post by yasoumalaka on 2006-09-28
Is there any risk/benefit to using ext3 with xfs for the swap?

---

### Post by halogen on 2006-09-28
> **yasoumalaka said:**
> Is there any risk/benefit to using ext3 with xfs for the swap?


It's not possible to have xfs as swap. 
Swap is it's own type of filesystem. You can format partitions as Fat, NTFS, XFS, JFS, EXT3, EXT2, Reiser ... etc.... or swap. 

Mixing filesystems (like ext3 and xfs) generally has reduced performance.

---

### Post by kurian on 2006-09-29
> **Paulo Wageck said:**
> i have been using reiserfs.... very stable and nice..
try it out.
good suggestions

---

### Post by yasoumalaka on 2006-09-29
I made an xfs partition then selected it as the swap. I don't know maybe it switched it or something. I'll check and write back.

---

### Post by ba5e on 2006-09-30
As mentioned before, SWAP is its 'own' unique file system sitting in a partition. You have simply converted an XFS partition to SWAP.

---

### Post by BUGabundo on 2007-05-08
I havent use Reiser for some time, but when I did, I found it quite fast.
Back to the present:
On my home PC, I have 4 drives, with dual boot.
So I have on my 200GBS WD 10GB NTFS (primary), swap, boot (ext3), / on XFS (extended), home on XFS (extended).
Two drives with NTFS, and a 500GBs Seagate Sata2 with XFS.

Since I got my brand new 500GBs SATA, I've been moving files (BIG and small) between disks. Using Konqueror, I could see speeds of about 20-30 MB per second.
I always assumed it was because of the [slow] older drives.
After running several hdparm tests on both drives and partitions I've found out that XFS as quite slower on those tests then NTFS or ext3.
My PATA drives range between 30 and 40 MB/s and the SATA can reach 68 MB/s (working on an external PCI controller as SATA 1).
But the speed of the partitions is quite different.
With some of my friends, I [tested]("http://groups.google.com/group/linuxnodei/browse_thread/thread/dd165bc2e08bd1a2/dc2bc1d2d432c062#dc2bc1d2d432c062") there speed and found mix results, expecially on the SWAP partition getting very mix results.

If everyone here could also post there results for the next command, we might get some more reliable results.
Here it is

sudo fdisk -l > ~/Desktop/fdisk.txt
## so we know the file system
sudo nice -n -20 hdparm -tTiT /dev/[h,s]d[a-z] > ~/Desktop/disks.txt
## Speed of the drives
sudo nice -n -20 hdparm -tT /dev/[h,s]d[a-z]? > ~/Desktop/part.txt
## Speed of the partitions

Please run test 2 and 3, 3 times or more and do an average, since the first two results tend to be very different.

Thanks so much.

---

### Post by Fraoch on 2007-05-09
> **BUGabundo said:**
> sudo fdisk -l > ~/Desktop/fdisk.txt
## so we know the file system

"Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4772    38331058+  83  Linux
/dev/hda2            4773        4865      747022+   5  Extended
/dev/hda5            4773        4865      746991   82  Linux swap / Solaris

Disk /dev/hdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        5222    41945683+   7  HPFS/NTFS
/dev/hdb2            5223       30401   202250317+   7  HPFS/NTFS"

Since hdb is NTFS and I can't write to it (couldn't get ntfs-3g working), I'll post the results for hda.

> sudo nice -n -20 hdparm -tTiT /dev/[h,s]d[a-z] > ~/Desktop/disks.txt
## Speed of the drives

"/dev/hda:

 Model=WDC WD400JB-00ENA0, FwRev=05.03E05, SerialNo=WD-WCAD19677204
 Config={ HardSect NotMFM HdSw>15uSec SpinMotCtl Fixed DTR>5Mbs FmtGapReq }
 RawCHS=16383/16/63, TrkSize=57600, SectSize=600, ECCbytes=40
 BuffType=DualPortCache, BuffSize=8192kB, MaxMultSect=16, MultSect=off
 CurCHS=4047/16/255, CurSects=16511760, LBA=yes, LBAsects=78165360
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 udma4 *udma5 udma3 udma4 *udma5 
 AdvancedPM=no WriteCache=enabled
 Drive conforms to: Unspecified:  ATA/ATAPI-1 ATA/ATAPI-2 ATA/ATAPI-3 ATA/ATAPI-4 ATA/ATAPI-5

 * signifies the current active mode

 Timing cached reads:   412 MB in  2.00 seconds = 205.56 MB/sec
 Timing buffered disk reads:  102 MB in  3.21 seconds =  31.82 MB/sec"

Run 2:

" Timing cached reads:   406 MB in  2.01 seconds = 202.27 MB/sec
 Timing buffered disk reads:   72 MB in  3.03 seconds =  23.78 MB/sec"

Run 3:

" Timing cached reads:   412 MB in  2.00 seconds = 205.63 MB/sec
 Timing buffered disk reads:  120 MB in  3.05 seconds =  39.38 MB/sec"

Average, cached = 204.49 MB/sec
Average, buffered = 31.66 MB/sec

> sudo nice -n -20 hdparm -tT /dev/[h,s]d[a-z]? > ~/Desktop/part.txt
## Speed of the partitions

Run 1:

"/dev/hda:
 Timing cached reads:   414 MB in  2.01 seconds = 206.13 MB/sec
 Timing buffered disk reads:   44 MB in  3.13 seconds =  14.06 MB/sec"

Run 2:

" Timing cached reads:   416 MB in  2.01 seconds = 207.45 MB/sec
 Timing buffered disk reads:  100 MB in  3.06 seconds =  32.64 MB/sec"

Run 3:

" Timing cached reads:   412 MB in  2.00 seconds = 205.56 MB/sec
 Timing buffered disk reads:   20 MB in  3.13 seconds =   6.39 MB/sec"

and since I got some abysmally low numbers, one more run to be sure:

Run 4:

"  Timing cached reads:   414 MB in  2.01 seconds = 206.13 MB/sec
 Timing buffered disk reads:   64 MB in  3.02 seconds =  21.22 MB/sec"

Average, cached = 206.32 MB/sec
Average, buffered = 18.58 MB/sec

Now, this disc is a cheap, fairly old 5400 RPM drive running on secondary hardware.  I'm commissioning the replacement for my primary hardware.  I would expect the results to be quite different: two SATA WD Raptors in mdadm RAID 0...I believe there'd be a bit of a performance boost there.:)

I'll post the results from that machine when I have time.

---

### Post by BUGabundo on 2007-05-09
> **Fraoch said:**
> Since hdb is NTFS and I can't write to it (couldn't get ntfs-3g working), I'll post the results for hda.


hdparm doesnt write on disks or partitions, it just do a reading test.
It would work even if the drive had no filesystem on it.
Please try again for the hdb.

about ntfs-3g: its quite easy to work with, although quite unstable when working with large files.
just try mounting it on the shell (without sudo):
ntfs-3g /dev/hdb1 /mnt/hdb1 -o uid=1000
ntfs-3g /dev/hdb2 /mnt/hdb2 -o uid=1000

if it works, just had the result of mtab to fstab

---

### Post by Fraoch on 2007-05-09
> **BUGabundo said:**
> hdparm doesnt write on disks or partitions, it just do a reading test.
It would work even if the drive had no filesystem on it.
Please try again for the hdb.

Ah, OK.

> sudo nice -n -20 hdparm -tTiT /dev/[h,s]d[a-z] > ~/Desktop/disks.txt
## Speed of the drives

"/dev/hdb:

 Model=SAMSUNG SP2514N, FwRev=VF100-33, SerialNo=S08BJ1GA102754
 Config={ Fixed }
 RawCHS=16383/16/63, TrkSize=34902, SectSize=554, ECCbytes=4
 BuffType=DualPortCache, BuffSize=8192kB, MaxMultSect=16, MultSect=off
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=66055248
 IORDY=on/off, tPIO={min:240,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 udma4 *udma5 udma3 udma4 *udma5 
 AdvancedPM=no WriteCache=enabled
 Drive conforms to: unknown:  ATA/ATAPI-1 ATA/ATAPI-2 ATA/ATAPI-3 ATA/ATAPI-4 ATA/ATAPI-5 ATA/ATAPI-6 ATA/ATAPI-7

 * signifies the current active mode

 Timing cached reads:   414 MB in  2.01 seconds = 206.27 MB/sec
 Timing buffered disk reads:  112 MB in  3.01 seconds =  37.17 MB/sec"

Run 2:

" Timing cached reads:   412 MB in  2.00 seconds = 205.64 MB/sec
 Timing buffered disk reads:   34 MB in  3.08 seconds =  11.04 MB/sec"

Run 3:

" Timing cached reads:   412 MB in  2.01 seconds = 205.13 MB/sec
 Timing buffered disk reads:  188 MB in  3.02 seconds =  62.26 MB/sec" (?)

and because I got some crazy-weird numbers there, run 4:

" Timing cached reads:   410 MB in  2.00 seconds = 204.94 MB/sec
 Timing buffered disk reads:  136 MB in  3.00 seconds =  45.29 MB/sec"

Average, cached = 205.50 MB/sec
Average, buffered = 38.94 MB/sec

> sudo nice -n -20 hdparm -tT /dev/[h,s]d[a-z]? > ~/Desktop/part.txt
## Speed of the partitions

"/dev/hdb:
 Timing cached reads:   420 MB in  2.00 seconds = 209.91 MB/sec
 Timing buffered disk reads:   28 MB in  3.00 seconds =   9.32 MB/sec"

Run 2:

" Timing cached reads:   420 MB in  2.01 seconds = 209.21 MB/sec
 Timing buffered disk reads:  184 MB in  3.01 seconds =  61.19 MB/sec"

Run 3:

" Timing cached reads:   414 MB in  2.00 seconds = 206.84 MB/sec
 Timing buffered disk reads:  210 MB in  3.02 seconds =  69.56 MB/sec"

and because there's even more crazy numbers there,

Run 4:

"  Timing cached reads:   412 MB in  2.01 seconds = 205.40 MB/sec
 Timing buffered disk reads:  142 MB in  3.03 seconds =  46.92 MB/sec"

Average, cached = 207.84 MB/sec
Average, buffered = 46.75 MB/sec

This is a much newer, much faster 7200 RPM drive.  I'm surprised the drive speed tests aren't that much faster.  I suspect I'm limited by CPU and the SiS 962L southbridge.

> about ntfs-3g: its quite easy to work with, although quite unstable when working with large files.
just try mounting it on the shell (without sudo):
ntfs-3g /dev/hdb1 /mnt/hdb1 -o uid=1000
ntfs-3g /dev/hdb2 /mnt/hdb2 -o uid=1000

if it works, just had the result of mtab to fstab

I kept getting errors about the drive being shutdown uncleanly.  That's quite possible, my old primary system failed under power.  I can't be bothered taking it out, mounting it in my USB drive enclosure, correctly shutting it down using my Windows laptop, uninstalling it from the enclosure and reinstalling it back in the case.  I'll reformat it to a Linux filesystem and recreate the data from a backup.

I will probably reformat it ext3.  It contains my music collection as well as a backup partition.  I don't need speed on it, I need reliability.

---

### Post by BUGabundo on 2007-05-09
> **Fraoch said:**
> ...
and because I got some crazy-weird numbers there, run 4:
...
This is a much newer, much faster 7200 RPM drive.  I'm surprised the drive speed tests aren't that much faster.  I suspect I'm limited by CPU and the SiS 962L southbridge.

I've seen pretty strange results when several runs are done, but you beat them all.
Something else is playing there. Are you sure that no other HEAVY application is running?
can you do the test on init 1? 
just run: sudo telinit 1. after tests are done, you can resume normal session with telinit 5.

also you only posted results of a single partition. where is hdb2?


> **Fraoch said:**
> 
I kept getting errors about the drive being shutdown uncleanly.  That's quite possible, my old primary system failed under power.  I can't be bothered taking it out, mounting it in my USB drive enclosure, correctly shutting it down using my Windows laptop, uninstalling it from the enclosure and reinstalling it back in the case.  I'll reformat it to a Linux filesystem and recreate the data from a backup.

I will probably reformat it ext3.  It contains my music collection as well as a backup partition.  I don't need speed on it, I need reliability.

that is quite usual.
just boot windows and run a chkdsk /f c: , or any other disk.

---

### Post by Fraoch on 2007-05-09
> **BUGabundo said:**
> I've seen pretty strange results when several runs are done, but you beat them all.
Something else is playing there. Are you sure that no other HEAVY application is running?

Not really, but this setup is very RAM-limited.  256 MB of DDR2100.  It gets pretty slow.  I'm commissioning its replacement as fast as I can, but it's not production-status at the moment.  I need to move hdb and some optical drives into it, get them working and reconfigure a server application.

> can you do the test on init 1? 
just run: sudo telinit 1. after tests are done, you can resume normal session with telinit 5.

also you only posted results of a single partition. where is hdb2?

That's a lot of testing because there's hda1, hda2, hda5, hdb1 and hdb2 to do.  I'll see what I can do, but this is known slow hardware.  I'd rather do testing on my new setup as time permits.  Hope you're not offended but that's quite a bit of testing if there were 3 or 4 runs for each of the 5 partitions. :(

> that is quite usual.
just boot windows and run a chkdsk /f c: , or any other disk.

The only Windows machine I have left is my company laptop.  I'd have to use my USB2 enclosure, remove the drive that's in that, install this one, etc. etc.  Not really worth it since I plan on reformatting it ext3 anyway.

---

### Post by Fraoch on 2007-05-09
OK, I re-ran all tests on all partitions 5 times on init 1.  I couldn't test hda2 because it kept giving me errors about being too small.

Also just realized that the drive tests should have been done on the drives hda and hdb and not on the partitions, but anyway.  I suppose if you average the separate partition tests it will work out as an overall average for the drives.

Testing on init 1 smoothed out the huge variations test-to-test I was getting.  The results test-to-test were very, very even, usually varying by +/- 1 MB/sec for cached tests and +/- 0.5 MB/sec for buffered tests.

hda1, drive tests:

Average, cached = 204.55 MB/sec
Average, buffered = 46.39 MB/sec

hda5, drive tests:

Average, cached = 205.54 MB/sec
Average, buffered = 26.75 MB/sec

hdb1, drive tests:

Average, cached = 205.70 MB/sec
Average, buffered = 63.02 MB/sec

hdb2, drive tests:

Average, cached = 205.86 MB/sec
Average, buffered = 62.47 MB/sec

hda1, partition tests:

Average, cached = 204.67 MB/sec
Average, buffered = 46.39 MB/sec

hda5, partition tests:

Average, cached = 205.89 MB/sec
Average, buffered = 26.76 MB/sec

hdb1, partition tests:

Average, cached = 205.82 MB/sec
Average, buffered = 62.83 MB/sec

hdb2, partition tests:

Average, cached = 205.70 MB/sec
Average, buffered = 62.78 MB/sec

As expected, my hdb is much faster than my hda, but I didn't think it would be that much faster.

---

### Post by hrp2171 on 2007-05-09
Tried XFS on my laptop, which is where I would like the most improvement in OS speed, but nothing to write home about happened.  I will try it on my home desktop sometime this week.:guitar:

---

### Post by md5hash on 2007-05-10
can you suggest a good partitioning heres what iam using

intel 1.6ghz, 720 ram
primary: 30gb ide
slave:20gb ide

---

### Post by BUGabundo on 2007-05-10
> **Fraoch said:**
> ... I couldn't test hda2 because it kept giving me errors about being too small.


thats because hda2 is the begining  of the extended partitions. it has no size.

about the test, they are meant to test both drives and partitions. thats why I provided to set of tests.And the reason of this topic: FS speed.

---

### Post by hrp2171 on 2007-05-10
> **md5hash said:**
> can you suggest a good partitioning heres what iam using

intel 1.6ghz, 720 ram
primary: 30gb ide
slave:20gb ide

Primary:
/dev/hda
    hda1 = /boot 100MB FS = ext3
    hda2 = /         10GB FS = xfs
    hda3 = /usr    aprox. 19GB  <- whatever's left after creating the other 2 FS = xfs

Slave:
/dev/hdb
    hdb1 = swap 720MB
    hdb2 = /home aprox. 19GB FS = xfs

My reasoning:  /usr is where most of the programs are going to get installed into.  You could make / smaller, too.  And other replies may make / smaller than my suggestion. /home is where I always download files from the net into.

If your processor is a Pentium 4 based CPU, don't forget to install the 686 kernel+restricted drivers from the repositories.  Also, if you have an nVidia or ATI video card, install the binary drivers from the repositories, too.

After reconfiguring my laptop to use xfs for /, installing the 686 stuff and the ATI driver, it is just as responsive as my tower unit.  That's even if I'm on batteries. :guitar:

---

### Post by md5hash on 2007-05-10
Thanks alot hrp2171... I'll try that

---

### Post by hrp2171 on 2007-05-10
> **md5hash said:**
> Thanks alot hrp2171... I'll try that

Also,  are  you going to be dual booting with Windows on that system?  Because my suggestion would have to tweaked accordingly. :confused:

---

### Post by md5hash on 2007-05-11
> **hrp2171 said:**
> Also,  are  you going to be dual booting with Windows on that system?  Because my suggestion would have to tweaked accordingly. :confused:

thanks its alot faster than before.. no i wll not use any windows os... :)

---

### Post by md5hash on 2007-05-25
i have a 80gb disk can you suggest a good partitioning scheme? thanks in advance..

---

### Post by omega_user on 2007-12-21
I vouch for XFS.  Athough this does seem a litte exaggerated, it's proven through benchmarks that Ext3 is the worst in both realiability and speed.  XFS and JFS are the best, only behind ZFS which, incredible as it is, is Sun proprietary.  A bonus for XFS is the extremely low fragmentation that occurs (yes there is fragmentation, just very little).  There is a way to defrag an XFS but it's not built in with Gnome, just like a bunch of other things aren't compatibile with XFS, like the partition editor.  LILO too, is the only booter that works with XFS, but people who want the GRUB solely because it shows the loading bar should forget about that and think how much faster it is.

---

### Post by articpenguin on 2008-03-17
The reason why ext3 takes forever to format is because its writing the inodes out. On my 750GB it took 20 mins just to create 300Million freakin inodes. Who the hell will use up 300Million?


Thats why i use JFS. Its both more fast and more reliable than ext3 IMO

---

### Post by alphacrux on 2008-04-10
Hey guys I did alot of research way back when I was formatting my drives to install Linux for the first time and here is what all I found about filesystems. First off XFS and JFS are not the fastest. ZFS is better all around, the newest version of Rieser is MUCH faster but very unstable, also ext2 beats just about all of them in speed as it doesn't use journaling which is why most people use it for their boot directory. Although ext3 is slower, it is rock solid as far as reliability goes. I've heard a few accounts of the xfs filesystem being corrupted when there is a power shortage. I do not think that slight performace is worth putting my drives at risk unless you are backing up your system on outside media anyway. If you really want performance then just put two hard drive in a raid 0 array, that will beat any change of filesystems. If there's one thing I'm not going to mess with its my filesystem.

Also ext3 is supported across ALL versions of Linux, I think some 60 or 70% of all Linux users use it. With that many people using it you can be assured that just about any and every Linux program, no matter how obscure and no matter its functionality, will not have any problems with this filesystem. Also I'm not too sure about further development about XFS but last I heard it might be kind of shady meaning there's no assurance that further work will be done on it, and if there is that it will be backwards compatible with the previous version of XFS. I know for a fact that the rieser filesystem development is having major problems. On the other hand ext4 is already set to be the next official filesystem for Debian and ubuntu after it comes out of development and is proven to be stable enough. Ext4 fixes almost all the performance problems ext3 had, is faster, and is backwards and forwards compatible with ext3. That means right now anyone with the ext3 filesystem can mount their drives as ext4 (of which the development version is available) and if they don't like it can remount it as ext3. I personally would choose reliablity and compatibility with future file systems. If I was using unix or solaris I'd go with ZFS but since that isn't an option here I'm sticking with ext3, anyways that's my two cents.

---

### Post by MonkeeSage on 2008-04-10
[A more recent benchmark set]("http://www.ffnn.nl/pages/articles/linux/server-wide-performance-benchmarking.php") (though all micro-benchmarks should be taken with a fairly large grain of salt) shows that ext3, in metadata journaling mode (data=writeback), performs competitively with XFS under a range of typical server loads (using [no]atime or APC apparently made little difference on either FS; see stats). Scroll to the bottom for the raw stats pdf file.

Similarly, a [benchmark set from a few years ago]("http://everything2.com/index.pl?node_id=1479435"), showed that on average, taking the best and weakest points of each system, they basically are all the same. One may excel in some job that another lags in, while the other beats the first in a different area. Or at least the numbers are close enough, on average, that they are not above the signal:noise threshold. The article also shows how to do some nice speed tweaks on XFS (which is its main purpose, BTW, the benchmarks are kind of incidental).

Ps. Just to clear up a point that someone said earlier: XFS doesn't "loose" data when the journal is not cleanly flushed. ext3, in full journal mode, gives you the last inodes that were journaled as file fragments (ordered journal mode is more complicated). XFS gives you the metadata only (which points to extents with a size but no data). When ext3 is in metadata journal mode, you get the same behavior -- XFS just had a bug that caused it to write nulls ("zeros") rather than freeing the extents. It is interesting to read [SGI's FAQ about XFS]("http://oss.sgi.com/projects/xfs/faq.html"), starting with the Q: "[Why do I see binary NULLS in some files after recovery when I unplugged the power?]("http://oss.sgi.com/projects/xfs/faq.html#nulls")"

All my partitions are ext3, BTW -- and hopefully ext4 soon, like the previous poster said! :)

---

### Post by articpenguin on 2008-04-11
Ext4 wont be out until at early 2009. E2fsprogs is still not extent ready for ext4.

---

### Post by MonkeeSage on 2008-04-11
BTW, it should be noted that with XFS or ext3 in metadata journal mode (data=writeback), and probably any other FS that journals metadata only (JFS?, reiser3/4 in some modes?), it is always a good idea to disable write caching on your drives (unless you're **absolutely sure** that they *really do* flush their caches on sync). You can do so by using the "write_cache = off" option in /etc/hdparm.conf (or the -W0 command line to hdparm).

---

