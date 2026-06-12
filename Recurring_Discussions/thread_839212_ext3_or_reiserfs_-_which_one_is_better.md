---
title: "ext3 or reiserfs - which one is better ?"
date: 2008-06-24
forum: Recurring Discussions
---

### Post by dexter.deepak on 2008-06-24
how can i , as a  user, evaluate the difference between ext3 and reiserfs filesystems ?
i am asking this because, i have been hearing reiserfs to be a better system, so i formatted one of my partitions to reiserfs and other to ext3 ...both 20 gb, but i still cant come to a conclusion.

---

### Post by henchman on 2008-06-24
I believe as a user, you won't experience any 'feeled' difference. Some benchmarks say that reiserfs shall be faster but then others are resulting in a heavy cpu-load of the upcoming reiserfs4... just to quote wikipedia:

> As of 2004, synthetic benchmarks performed by Namesys show that Reiser4 is 10 to 15 times faster than its most serious competitor ext3 working on files smaller than 1 KiB. Namesys's benchmarks suggest it is typically twice the performance of ext3 for general-purpose filesystem usage patterns.[3] Other benchmarks show results of Reiser4 being slower on many operations.[4]

so you shouldn't really care if you do not want to do something very special :) ext3 is the most widely spread filesystem and the default in ubuntu, so imho just use it

---

### Post by xlinuks on 2008-06-24
Fat16

---

### Post by erginemr on 2008-06-24
Here is my two cents: 

I have also heard that reiserfs performs slightly faster in some file I/O tests, but have also heard that it is less reliable. Some Linux users in the forums or elsewhere have reported to lose their partition and valuable data with reiserfs, where ext3 was rock-stable...

---

### Post by _sphinx_ on 2008-06-24
> **xlinuks said:**
> Fat16

I think fat32 OR (16) has this problem that you cant' have a file greater that 4GB. Also my exprience with fat32 was bad since it was slow as compared to ext3.

---

### Post by henchman on 2008-06-24
hm... i belive this was irony :popcorn:

> Some Linux users in the forums or elsewhere have reported to lose their partition and valuable data with reiserfs, where ext3 was rock-stable...

i have heard that sometimes when the fs is litte broken, fsck even breaks the fs more up when using reiserfs - so ext3 seems to be a bit more mature

---

### Post by _sphinx_ on 2008-06-24
> **henchman said:**
> 
i have heard that sometimes when the fs is litte broken, fsck even breaks the fs more up when using reiserfs

:lolflag:

---

### Post by nvteighen on 2008-06-24
And how is this related to usual programming? Unless you're doing something very very but very low-level so that your nose is actually touching the motherboard :), you shouldn't be concerned by this when developing a regular, normal application.

---

### Post by LaRoza on 2008-06-24
> **_sphinx_ said:**
> I think fat32 OR (16) has this problem that you cant' have a file greater that 4GB. Also my exprience with fat32 was bad since it was slow as compared to ext3.

FAT32 is limitted by file sizes of 4 GB

FAT12: 32 MB (The entire partition)

FAT16: Limitted at 2 GB for the entire partition

---

### Post by WW on 2008-06-24
Isn't this really a question for the "General Help" forum, or maybe "Installation and Upgrades" (since one usually confronts the question of which file system to use during installation)?

---

### Post by erginemr on 2008-06-24
> **xlinuks said:**
> Fat16

I also believe this was a joke. :KS

---

### Post by xlinuks on 2008-06-24
> **_sphinx_ said:**
> I think fat32 OR (16) has this problem that you cant' have a file greater that 4GB. Also my exprience with fat32 was bad since it was slow as compared to ext3.
was just a stupid joke of mine :)

---

### Post by dexter.deepak on 2008-06-24
> **_sphinx_ said:**
> The best experience you can ever have with programming is: Segmentation fault (core dumped)

apart from the topic...i seem to have experienced this error somewhere before...can you please explain what it means..in relation to the present context ?

---

### Post by LaRoza on 2008-06-24
> **dexter.deepak said:**
> apart from the topic...i seem to have experienced this error somewhere before...can you please explain what it means..in relation to the present context ?

[http://en.wikipedia.org/wiki/Segmentation_fault](http://en.wikipedia.org/wiki/Segmentation_fault)

What does this thread have to do with programming?

---

### Post by Zugzwang on 2008-06-24
> **dexter.deepak said:**
> apart from the topic...i seem to have experienced this error somewhere before...can you please explain what it means..in relation to the present context ?

You can look up what that means here: [http://ubuntuforums.org/showthread.php?t=815055]("http://ubuntuforums.org/showthread.php?t=815055"). However, there is no relation to the currect context. If you experienced this error while running some program doing operations on a filesystem, then the program is likely to have a bug.

---

### Post by dexter.deepak on 2008-06-24
sorry for deviating apart..but now i just wanted to know what it means..i have experienced this error a lot while using compiz on gutsy..so i was being curious.

---

### Post by LaRoza on 2008-06-24
> **dexter.deepak said:**
> sorry for deviating apart..but now i just wanted to know what it means..i have experienced this error a lot while using compiz on gutsy..so i was being curious.

I mean, the entire thread. It is just another file system comparison. Moved.

---

### Post by smartboyathome on 2008-06-24
I am now using ext3, but that is because fsck is now stoppable on my laptop. Before then, I just got faster file systems with ReiserFS due to fsck coming up every 10 boots due to me having multiple partitions.

---

### Post by bodhi.zazen on 2008-06-24
> **LaRoza said:**
> I mean, the entire thread. It is just another file system comparison. Moved.

LOL

> **dexter.deepak said:**
> how can i , as a  user, evaluate the difference between ext3 and reiserfs filesystems ?
i am asking this because, i have been hearing reiserfs to be a better system, so i formatted one of my partitions to reiserfs and other to ext3 ...both 20 gb, but i still cant come to a conclusion.

Start by asking yourself, what is it you are evaluating the file system for. Speed ? Stability ? cross platform compatibility ? features ? lots of small files ? networking ? large files ?

[http://www.linux.com/feature/31939](http://www.linux.com/feature/31939)

---

### Post by jrusso2 on 2008-06-24
> **erginemr said:**
> Here is my two cents: 

I have also heard that reiserfs performs slightly faster in some file I/O tests, but have also heard that it is less reliable. Some Linux users in the forums or elsewhere have reported to lose their partition and valuable data with reiserfs, where ext3 was rock-stable...

For me the only times I have ever lost data was when I was using ext2 or ext3.  Reiser has been very stable but lately I have been using JFS for / and XFS for /home at it seems to be a good combination.

---

### Post by LaRoza on 2008-06-25
> **bodhi.zazen said:**
> LOL


It was originally in programmint talk for some reason...

---

### Post by articpenguin on 2008-06-25
JFS it uses B+ trees extensionally.

---

### Post by Foster Grant on 2008-06-30
Reiser *kills* ext. Of course, if you can't find your files ... heck, they might be in Russia or something. Who knows?

Of course, eventually you open up your computer and you discover that your hard drive has been removed and the rest of your PC has been carefully cleaned, although there's still an inch of water sloshing around.

[size=1]And I'm stunned &#8212; stunned, I tell you! &#8212; that nobody else has gone there yet.[/size]

---

### Post by articpenguin on 2008-07-01
reiserfs should be renamed to Murderfs since mr.Reiser is in jail:)

---

### Post by LaRoza on 2008-07-01
> **articpenguin said:**
> reiserfs should be renamed to Murderfs since mr.Reiser is in jail:)

Why? Mr. Reiser's name hasn't changed.

---

### Post by ryaxnb on 2008-07-03
> **_sphinx_ said:**
> I think fat32 OR (16) has this problem that you cant' have a file greater that 4GB. Also my exprience with fat32 was bad since it was slow as compared to ext3.

I like FAT32 and I liked the days when Linux could boot and root from it. <Grumpyoldman> I like simple FSes, dead simple. </Grumpyoldman> I wish there was a SuperFAT with UNIX permissions, NT ACLS, and files greater then 4GB. That is the only additions I want, and I want greater then 4G files to be split across multiple 4G files so that computers running old Windows DOS and other FAT32 compliant apps can still read/write the volume, boot from it, and even split/unsplit the files onto another volume.

---

### Post by hugmenot on 2008-07-04
There are many reports around that reiserfs ***** up the file system in case of unclean reboots, bad blocks, and so on. And I have to say I experienced the complete opposite with the many failing hard drives I had in the last years.
I had head crashes with many hundred bad blocks before and I was able to recover most  of the files with reiserfsck --rebuild-tree. For the lost entries it preserves many file names in lost+found afterwards, so that is helpful.

Prologue: Since last year I have very serious problems with the ATA controller in my 4 year old laptop. It has some electrical problems such that suddenly the power to the hard disk is interrupted, there's a whistle noise and the hdd spins down, I see scary stuff in dmesg, but often the disk will spin up again. But a fraction of the times the complete system will immediately lock up (mouse cursor frozen, no Alt+SysReq anymore), and I have to power cycle.

This has happened a few dozen times already, and Reiserfs has always come up properly after replaying the journal. No data loss besides bash history. And I have / and /home on reiserfs.

I really don&#8217;t see how people can claim that reiserfs is dangerous.

---

### Post by JonathanRRogers on 2008-07-07
I must also reply that problems with reliability of reiserfs (version 3) are greatly exaggerated. I've been using it for most of my filesystems for many years and have not lost any more data on reiserfs filesystems than ext2 or ext3. When I've lost data, I have usually identified faulty hardware, faulty software unrelated to the filesystem, or my own mistakes as the cause. No filesystem feature is a substitute for backups on an independent system.

I think it's unfortunate that most distributions, including Ubuntu still use ext2 or ext3 by default, since JFS, XFS, and reiserfs all perform better, are at least as reliable, and are at least as mature.

I've recently been running bonnie++ benchmarks on my machine and confirmed what I've been reading for some years: XFS performs very well for streaming reads and writes to large files, reiserfs performs extremely well on small files, and both beat ext3 on just about everything. IMHO, reiserfs is currently the best choice for general purpose filesystems, and XFS and JFS are also excellent choices.

Another important factor in filesystem performance that isn't discussed enough is atime updates. Very few applications depend on it, but it slows down all filesystem operations significantly. One only has to mount a filesystem (any type) with the "noatime" option to avoid this penalty. Ubuntu is now using the newer "relatime" option, which probably performs as well as "noatime" but is more compatible with applications that depend on atime. Switching from the default atime update mode to either "noatime" or "relatime" probably increases performance more than switching from ext3 to reiserfs or anything else.

---

### Post by Frak on 2008-07-07
Except for mounting speeds, I find ReiserFS to be clearly better.

---

### Post by bodhi.zazen on 2008-07-07
> **JonathanRRogers said:**
> I must also reply that problems with reliability of reiserfs (version 3) are greatly exaggerated. I've been using it for most of my filesystems for many years and have not lost any more data on reiserfs filesystems than ext2 or ext3. When I've lost data, I have usually identified faulty hardware, faulty software unrelated to the filesystem, or my own mistakes as the cause. No filesystem feature is a substitute for backups on an independent system.

I think it's unfortunate that most distributions, including Ubuntu still use ext2 or ext3 by default, since JFS, XFS, and reiserfs all perform better, are at least as reliable, and are at least as mature.

I've recently been running bonnie++ benchmarks on my machine and confirmed what I've been reading for some years: XFS performs very well for streaming reads and writes to large files, reiserfs performs extremely well on small files, and both beat ext3 on just about everything. IMHO, reiserfs is currently the best choice for general purpose filesystems, and XFS and JFS are also excellent choices.

Another important factor in filesystem performance that isn't discussed enough is atime updates. Very few applications depend on it, but it slows down all filesystem operations significantly. One only has to mount a filesystem (any type) with the "noatime" option to avoid this penalty. Ubuntu is now using the newer "relatime" option, which probably performs as well as "noatime" but is more compatible with applications that depend on atime. Switching from the default atime update mode to either "noatime" or "relatime" probably increases performance more than switching from ext3 to reiserfs or anything else.

FYI, realtime is now the default with Ubuntu 8.04 (check out fstab :twisted:

for those wondering about noatime and relatime :

[http://lwn.net/Articles/244829/](http://lwn.net/Articles/244829/)

---

### Post by JonathanRRogers on 2008-07-07
> **bodhi.zazen said:**
> FYI, realtime is not the default with Ubuntu 8.04 (check out fstab :twisted:

for those wondering about noatime and relatime :

[http://lwn.net/Articles/244829/](http://lwn.net/Articles/244829/)

The /etc/fstab on my freshly installed Ubuntu 8.04 system is where I found relatime and I didn't put it there. Perhaps you did?

---

### Post by bodhi.zazen on 2008-07-07
> **JonathanRRogers said:**
> The /etc/fstab on my freshly installed Ubuntu 8.04 system is where I found relatime and I didn't put it there. Perhaps you did?

:lolflag: got to love the typos

---

### Post by JonathanRRogers on 2008-07-07
> **bodhi.zazen said:**
> FYI, realtime is not the default with Ubuntu 8.04 (check out fstab :twisted:

for those wondering about noatime and relatime :

[http://lwn.net/Articles/244829/](http://lwn.net/Articles/244829/)

For those wondering about the status of relatime in Ubuntu 8.04:
[https://wiki.ubuntu.com/HardyHeron/Beta#head-864ed7d06d611780963dc0cd8d78c8b55b08b952](https://wiki.ubuntu.com/HardyHeron/Beta#head-864ed7d06d611780963dc0cd8d78c8b55b08b952)

---

### Post by sdennie on 2008-07-07
Actually, you don't even need to specify relatime in /etc/fstab.  In 8.04 it will automatically mount ext3 partitions with relatime.  See: [http://ubuntuforums.org/showpost.php?p=5257069&postcount=3](http://ubuntuforums.org/showpost.php?p=5257069&postcount=3).

---

### Post by bodhi.zazen on 2008-07-07
> **vor said:**
> Actually, you don't even need to specify relatime in /etc/fstab.  In 8.04 it will automatically mount ext3 partitions with relatime.  See: [http://ubuntuforums.org/showpost.php?p=5257069&postcount=3](http://ubuntuforums.org/showpost.php?p=5257069&postcount=3).

vor is mount impaired :twisted:

```
mount | grep ext3
```

---

