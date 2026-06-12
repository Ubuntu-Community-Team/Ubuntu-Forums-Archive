---
title: "Fragmentation"
date: 2009-03-19
forum: Recurring Discussions
---

### Post by randalph on 2009-03-19
No no no! Ext3 (and every filesystem) can and will eventually fragment. Ext3 is better than e.g. FAT but it's not impervious to fragmentation. See this post: [http://ubuntuforums.org/showpost.php?p=6776092&postcount=19](http://ubuntuforums.org/showpost.php?p=6776092&postcount=19)

please search the forums before posting.
please don't repeat the myth that ext3 doesn't fragment.

---

### Post by philinux on 2009-03-20
Ext3 does fragment but nowhere near the scale of winblows. That is only relevant to server systems handling very large files. Normal Desktop users will not experience this.

---

### Post by odanawt on 2009-03-20
> **k3lt01 said:**
> Check out [this thread]("http://ubuntuforums.org/showthread.php?t=140920"), it should give you some tips for cleaning up. As for defragmenting, like the others have said its not required.

That was extremely helpful! :D You learn something new everyday around here.

---

### Post by InfectedWithDrew on 2009-03-20
About reading ext2/ext3 file systems from Windows, I recommend ext2fsd.

----------------
Now playing: [Submersed - Rewind](http://www.foxytunes.com/artist/submersed/track/rewind)

---

### Post by randalph on 2009-03-20
> **philinux said:**
> Ext3 does fragment but nowhere near the scale of winblows. That is only relevant to server systems handling very large files. Normal Desktop users will not experience this.

You are simply wrong that normal users will not experience it. Ext3 fragmentation is a known real issue that has been studied and documented by actual filesystem researchers [https://ols2006.108.redhat.com/2007/Reprints/sato-Reprint.pdf](https://ols2006.108.redhat.com/2007/Reprints/sato-Reprint.pdf) which is why they are building an online defragmenter into ext4.
Fragmentation on media boxes (e.g. running MythTV is a real issue (I and at least one other poster in the thread I linked to above personally experienced it) and it's best practice on such systems to run XFS so that they can be defragmented. filesystems might fragment slower these days but we also expect our distros to last longer than 6 months before a wipe & reinstall. Once ext3 fragments there's nothing you can do about it except start over.

---

### Post by davo11 on 2009-03-20
you don't need to
this is one of the major differences between windows and linux
windows is lazy - it stores parts of files all of the place automatically
linux is careful - it stores parts of files all together
so no need to defrag or anything else

---

### Post by randalph on 2009-03-20
> **davo11 said:**
> you don't need to
this is one of the major differences between windows and linux
windows is lazy - it stores parts of files all of the place automatically
linux is careful - it stores parts of files all together
so no need to defrag or anything else

You are wrong. You do need to defragment if you want your systems to last longer than a year. please run the tests here [http://ubuntuforums.org/showpost.php?p=6776092&postcount=19](http://ubuntuforums.org/showpost.php?p=6776092&postcount=19) and read the redhat whitepaper I linked to above to educate yourself rather than repeating mantras you heard. Note that Ext4 devs are building in online defragmentation - did they somehow forget some magic algorithm that went in ext3? Hint: No.

---

### Post by TheUnderTaker on 2009-03-20
I know they fragment which why i said there allocation schemes reduce fragmentation compared to NTFS and fat32.


Here is proof ext3 fragments on a 3 day old filesystem with 50% disk space used

  160881 inodes used (40.55%)
     798 non-contiguous files (0.5%)
     179 non-contiguous directories (0.1%)

---

### Post by mcduck on 2009-03-20
> **TheUnderTaker said:**
> I know they fragment which why i said there allocation schemes reduce fragmentation compared to NTFS and fat32.


Here is proof ext3 fragments on a 3 day old filesystem with 50% disk space used

  160881 inodes used (40.55%)
     798 non-contiguous files (0.5%)
     179 non-contiguous directories (0.1%)

It's not that Ext wouldn't fragment. It simply fragments much less, and the fragmentation that happens has much smaller impact on performance. To the level where it stops being something you'd ever need to worry about in normal use. Only if your drive is almost completely full, or you are running a server under heavy load and disk access.

0.5% non-contiguous files is absolutely meaningless.

Even if you manage to get it up to as high as 22% (which I've done on one of the drives on my 3D rendering/video workstation) it still won't have any effect in the drives performance. I know it doesn't, I ran performance tests when I noticed how high the amount of non-contiguous files was when compared to any  of my other Linux drives. I doubt that you could get that much fragmentation on any normal desktop use, all my other drives have less than 5% non-contiguous files.

---

### Post by randalph on 2009-03-20
> **mcduck said:**
> It's not that Ext wouldn't fragment. It simply fragments much less, and the fragmentation that happens has much smaller impact on performance. To the level where it stops being something you'd ever need to worry about in normal use. Only if your drive is almost completely full, or you are running a server under heavy load and disk access.

0.5% non-contiguous files is absolutely meaningless.

Even if you manage to get it up to as high as 22% (which I've done on one of the drives on my 3D rendering/video workstation) it still won't have any effect in the drives performance. I know it doesn't, I ran performance tests when I noticed how high the amount of non-contiguous files was when compared to any  of my other Linux drives. I doubt that you could get that much fragmentation on any normal desktop use, all my other drives have less than 5% non-contiguous files.

Yes the 0.5% number is indeed meaningless since 1. it's on a 3 day old drive 2. fsck fragmentation percentage only gives you the ratio of fragmented files to total files without including how fragmented they are, 3. all the zero-byte files like in /dev are included in the total count but will obviously never fragment, and 4. even if it's a small percentage, those that have fragmented badly could be frequently-accessed files that a user is waiting for interactively.

Please run the very simple tests in my forum link above on your video workstation and post how many fragments are created and the age, use & specs of your filesystem. Find the total access time specs for your drive and multiply by the number of fragments. While you're at it also run filefrag on a couple of your reasonably large, recently created videos. I detailed exactly how you can demonstrate and quantify fragmentation. Please tell us what specifically are these performance tests you ran to convince yourself that it wasn't an issue. The linux symposium paper I linked to measures a 15% degradation in total file read times due to multiple stream writes.

---

### Post by Sir Jasper on 2009-03-20
Hi guys,

This may not be at all relevant to defragmentation but suppose that I take a logical image (as opposed to a 1 to 1 clone) then my understanding (which might well be mistaken) is the empty spaces will not be recorded.

If that image is cloned back then whilst it may not be defragmented, contiguous free space may be maximised but then, even if I am right, I am not at all sure this is ideal.

I would like to learn more with, ideally for me, a not too technical response.

My regards

---

### Post by randalph on 2009-03-20
> **Sir Jasper said:**
> Hi guys,

This may not be at all relevant to defragmentation but suppose that I take a logical image (as opposed to a 1 to 1 clone) then my understanding (which might well be mistaken) is the empty spaces will not be recorded.

If that image is cloned back then whilst it may not be defragmented, contiguous free space may be maximised but then, even if I am right, I am not at all sure this is ideal.

I would like to learn more with, ideally for me, a not too technical response.

My regards

Hey yeah doing a cp or rsync to a new drive should set you up with a defragmented drive. It's obviously much easier to run a defrag utility though if your filesystem is defragmentable. But if you think a non-defragmentable filesystem is fragmented & killing your performance this is pretty much what you need to do. Mind the ownership & permissions & you need to change the UUIDs in /etc/fstab and /boot/grub/menu.lst to use your new drive's UUID.

edit: if you're doing the clone back to the original drive, you need to first delete all the stuff off of it first for it to reduce fragmentation; if you just write it back with the files in-place, it'll just keep the existing extents (fragments) and won't fix anything. It's probably better to just do a single clone to a new drive & use that, then at least you have the original as a failsafe until you confirm the new one works.

---

### Post by lisati on 2009-03-20
The "defrag or not" recurring discussion is a bit like the "antivirus or not" recurring discussion: most of the time it (fragmentation/malware/whatever) isn't a real problem in Ubuntu (and thus shouldn't be worried about too much), but "stuff" can still happen.

---

### Post by Sir Jasper on 2009-03-20
Hi randalph,

Thank you for your help and especially for your edit on cloning back to the same drive.

I read that Ubuntu starts in the middle of the drive and then expands by writing on either side with extra space for yet more data.

However, if a logical image (i.e. without spaces) were cloned back using a cloning program it seems everything would be at the beginning of the drive (or partition).

Is this correct and more importantly might it matter?

My regards

---

### Post by SunnyRabbiera on 2009-03-20
You realize though that it is very hard to fragment ext3, its a good filesystem and only fragments when you use up too much filespace.
But for the common desktop user its not likely a concern, for servers maybe but seriously the Ext filesystem family is better at handling itself then NTFS or FAT

---

### Post by bodhi.zazen on 2009-03-20
Yikes, this whole conversation was (IMO) off topic and qualifies for a recurring discussion.

> **mcduck said:**
> It's not that Ext wouldn't fragment. It simply fragments much less, and the fragmentation that happens has much smaller impact on performance. To the level where it stops being something you'd ever need to worry about in normal use. Only if your drive is almost completely full, or you are running a server under heavy load and disk access.

0.5% non-contiguous files is absolutely meaningless.

Even if you manage to get it up to as high as 22% (which I've done on one of the drives on my 3D rendering/video workstation) it still won't have any effect in the drives performance. I know it doesn't, I ran performance tests when I noticed how high the amount of non-contiguous files was when compared to any  of my other Linux drives. I doubt that you could get that much fragmentation on any normal desktop use, all my other drives have less than 5% non-contiguous files.

What mcduck said :)

The "facts" are (not that they are in any order or make sense) :

1. No file system is completely free from fragmentation.

2. Fragmentation on ext3 occurs, but (depending on how you define a "performance hit" , see below) it does not typically result in a performance hit. Typically fragmentation occurs most often with things such as torrents and the disk being full.

3. ext4 does in fact have both fragmentation and an online defragmentation tool. It is not yet implemented by default in Ubuntu 9.04 (although you can use ext4).

4. Other defragmentation tool are available for other file systems.

5. Most users do not need to be concerned with fragmentation.

6. Most of the discussion on fragmentation is infact ext3 vs say NTFS. NTFS will fragemnt over time to the point where disk I/O performance drops appreciabley and linux native file systems are an order of magintiude better.

7. Yes, fragmentation can affect performance on linux file systems.

=========

To give you an example, on Windows partitions fragmentation of the file system can be as high as 18000 (yes **18 thousand) percent**.

If you are interested may I suggest you read the white papers ?

[http://74.125.95.132/search?q=cache:ZnivZZD-UisJ:www.kernel.org/doc/ols/2006/ols2006v1-pages-193-208.pdf+file+system+fragmentation+performance&cd=38&hl=en&ct=clnk&gl=us](http://74.125.95.132/search?q=cache:ZnivZZD-UisJ:www.kernel.org/doc/ols/2006/ols2006v1-pages-193-208.pdf+file+system+fragmentation+performance&cd=38&hl=en&ct=clnk&gl=us)

[http://www.eecs.harvard.edu/~keith/research/tr94.html](http://www.eecs.harvard.edu/~keith/research/tr94.html)

Part of the "problem" is in defining "acceptable" performance. If you tolerate no performance degradation in disk I/O due to fragmentation, well that will be difficult to impossible to achieve with any file system.

If you find say 20-30 % degradation "acceptable" ext3 and in fact most, if not all linux file systems are acceptable.

Both FAT and NFTS have performance degration much much higher then 20-30 %

So you see, you are all right and it is all relative :twisted:

---

### Post by Twitch6000 on 2009-03-20
> **randalph said:**
> You are simply wrong that normal users will not experience it. Ext3 fragmentation is a known real issue that has been studied and documented by actual filesystem researchers [https://ols2006.108.redhat.com/2007/Reprints/sato-Reprint.pdf](https://ols2006.108.redhat.com/2007/Reprints/sato-Reprint.pdf) which is why they are building an online defragmenter into ext4.
Fragmentation on media boxes (e.g. running MythTV is a real issue (I and at least one other poster in the thread I linked to above personally experienced it) and it's best practice on such systems to run XFS so that they can be defragmented. filesystems might fragment slower these days but we also expect our distros to last longer than 6 months before a wipe & reinstall. Once ext3 fragments there's nothing you can do about it except start over.
In some ways you are right yet others you are wrong.

You are right by saying yes ext3 and ext2 defrags and this is a fact I do not care what others say it is a fact.

However you are wrong by saying if it fragments you HAVE TO reinstall.

This is false many people have made defragging programs for Linux. Mainly the ext2 and 3 filesystems.

I know a person from the debian forums made a decent ext2 defragger.

I also seen a few months ago someone from here made a multi defragger.

So please do not spread fud...

---

### Post by randalph on 2009-03-20
Based on publishing of benchmarks, RAID striping, SSD performance interest, as well as the frequency of this topic in the forums, I would say that the Linux community is interested in drive performance, and I think many would say that a 20-30% drop in disk read speeds due to fragmentation after a year that continues to worsen is not something that they would like, especially when there are defragmentable filesystems like XFS. People go to far more trouble to overclock or tune their systems to get less than a 20-30% boost on stuff and filesystem decisions get made off of far fewer benchmark percentage points than that. Unfortunately benchmarks tend to be done on freshly formatted drives so the long term degredation of non-defragmentable filesystems like ext3 isn't exposed.

So yeah, everyone: look at Figure 4 in bodhi.zazen's first link. multi-threaded write performance results showed 20% drop in read speed after 2500 concurrent files written, and appears that it would continue decreasing. Happens faster with 4 concurrent write threads. That's the fragmentation that you get. If you think that that's negligible, feel free to continue using ext3 but 1. know that it's happening and 2. please stop telling people that it isn't, especially when they ask. yes it's better than FAT/NTFS but that's absolutely not the point. Put XFS or ext4 on that plot with a defrag cronjob and it'll perform the same at 2500 files as on 1. I personally prefer XFS over ext4 right now since it's been more thouroughly tested.

aside: comparing 18000% NTFS vs. 22% or 0.5% EXT3 is apples-and-oranges due to the method of computing fragmentation as I noted above. the way fsck counts it's impossible for it to report more than 100%.

---

### Post by bodhi.zazen on 2009-03-20
You are welcome to your opinions, and I respect you and your opinions.

But you speak for yourself and not the Ubuntu or FOSS communities and there are many who find a 30 % decrease "acceptable".

When a better file system comes out, with less fragmentation, such as ext4, I am sure many if not most will switch.

Benchmarks should NOT be the only consideration when selecting a file system and there are other features to consider.

I would be interested to see you stop your ranting, it is not very convincing to me, and ask you please tell us what, in your opinion, is the best file system any why. Otherwise it appears as if you are ranting without offering any solutions.

Please include information such as fragmentation, file system tools, benchmarks, and other features such as support for acl or what have you.

Certainly you are not implying that NTFS is a better file system with less fragmentation and better performance and features for Linux users.

My preference is ext4, although there are still some stability issues. When those are solved I see ext4 as one of the better options.

---

### Post by TheUnderTaker on 2009-03-20
I know .5% fragmentation is nothing. my /home partition is 4 months old and is 2% fragmented.


/home/john/.jagex_cache_32/runescape/main_file_cache.idx7: 60 extents found, perfection would be 1 extent
/home/john/.mozilla/firefox/c5c3yf3j.default/urlclassifier3.sqlite: 29 extents found, perfection would be 1 extent

Those too are my most fragmented files.

---

### Post by MikeTheC on 2009-03-21
I believe in fragmentation. I also believe I'll have another beer.

---

