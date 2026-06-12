---
title: "Defragmentation"
date: 2008-07-14
forum: Recurring Discussions
---

### Post by hidarikani on 2008-07-14
I used to defragment NTFS partitions from time to time when I was using XP.

What about ext3?

---

### Post by justleen on 2008-07-14
There is no need to defragment a ext3 filesystem
> That being said, as the Linux System Administrator Guide states, "Modern Linux filesystem(s) keep fragmentation at a minimum by keeping all blocks in a file close together, even if they can't be stored in consecutive sectors. Some filesystems, like ext3, effectively allocate the free block that is nearest to other blocks in a file. Therefore it is not necessary to worry about fragmentation in a Linux system."
see [http://en.wikipedia.org/wiki/Ext3](http://en.wikipedia.org/wiki/Ext3) for more info.

---

### Post by knutschr on 2008-07-14
Why ext3 isn't defragmented is explained in more detail here:
[http://www.whylinuxisbetter.net/items/defragment/index.php](http://www.whylinuxisbetter.net/items/defragment/index.php)

---

### Post by hyper_ch on 2008-07-14
as said by the previous responders, there's no need to defrag on linux.

---

### Post by Sukarn on 2008-07-14
The argument that "there is no need to defragment Linux filesystems" arises from ignorance and pride of Linux users. There are cases where defragmentation is needed, but its plainly ignored.

Every filesystem in the world gets fragmented at some point or the other. It cannot be helped, unless you want the filesystem to move around files to make continuous space for a new file every time you make new files. This is because people create and delete files all the time, and empty spaces in between are created as a result of deletion of old files.

Granted, its need is not as high in Linux in terms of performance as it is in Windows, but the need is still there in other cases.

For example, if I want to recover a deleted file from an ext3 filesystem, I end up recovering only the first chunk. All other chunks of data that are spread out all over the filesystem just get lost.

A fsck of my storage filesystem (60.00 GB) shows that its got 24.31% fragmented data. I don't care much about this as its mostly filled with videos of TV shows and movies, but if I was to delete something important there by mistake, chances are that I would end up recovering a small part of what I lost because of the fragmentation and how ext3 is designed.

The upcoming ext4 has got better functionality. At least someone out there recognizes that ignoring a problem and saying that it does not exist will not solve the problem.

---

### Post by mcduck on 2008-07-14
> **Sukarn said:**
> The argument that "there is no need to defragment Linux filesystems" arises from ignorance and pride of Linux users. There are cases where defragmentation is needed, but its plainly ignored.

Every filesystem in the world gets fragmented at some point or the other. It cannot be helped, unless you want the filesystem to move around files to make continuous space for a new file every time you make new files. This is because people create and delete files all the time, and empty spaces in between are created as a result of deletion of old files.

Granted, its need is not as high in Linux in terms of performance as it is in Windows, but the need is still there in other cases.

For example, if I want to recover a deleted file from an ext3 filesystem, I end up recovering only the first chunk. All other chunks of data that are spread out all over the filesystem just get lost.

A fsck of my storage filesystem (60.00 GB) shows that its got 24.31% fragmented data. I don't care much about this as its mostly filled with videos of TV shows and movies, but if I was to delete something important there by mistake, chances are that I would end up recovering a small part of what I lost because of the fragmentation and how ext3 is designed.

The upcoming ext4 has got better functionality. At least someone out there recognizes that ignoring a problem and saying that it does not exist will not solve the problem.
You are confusing file system fragmentation with file fragmentation.. ;)

The problem you describe would be a result of file fragmentation (files being fragmented to small pieces around the file system). Linux filesystems avoid that by allowing more file system fragmentation (files being spread around the file system, but keeping one file as one piece).

File system fragmentation is pretty much meaningless when it comes to drive performance, as the files are still in one piece and can thus be read without any extra disc seeking.

---

### Post by CatKiller on 2008-07-14
> **hidarikani said:**
> I used to defragment NTFS partitions from time to time when I was using XP.

What about ext3?

Realistically, all filesystems will become fragmented over time. Unless you only ever add files, and never delete or modify existing ones, of course.

Unfortunately, Windows filesystems also fragment the files themselves, which is why you get such a performance penalty from running Windows on a fragmented filesystem, and have to defragment the drive from time to time. Linux doesn't do this.

Files can still become fragmented if the filesystem becomes *really* full and there is nowhere to put the files that keeps them intact. It doesn't happen in general use, though.

If you want your Linux filesystem to be defragmented, possibly because it's been full in the past, the generally preferred method is to back the data up somewhere using **tar** or **cp**, delete and re-create the partition, and then restore the data from your backup.

Most people will not need to do this, though.

---

### Post by Jim! on 2008-07-14
> Once an ext3 reaches 85-90% capacity it starts to fragment because space is starting to run out. 

Ext3 does indeed fragment and those that deny this fact and say that Ext3 doesn't need to be defragmented are being stubborn.

---

### Post by CatKiller on 2008-07-14
> **Jim! said:**
> Ext3 does indeed fragment and those that deny this fact and say that Ext3 doesn't need to be defragmented are being stubborn.

No. **Files** do not fragment **much** in **general usage**. A full filesystem is a special case, and is much more of an issue in itself than the fact that it will also fragment files.

Those that deny this fact and say that ext3 needs to be defragmented fail at reading comprehension.

---

### Post by Jim! on 2008-07-14
> **CatKiller said:**
> No. **Files** do not fragment **much** in **general usage**. A full filesystem is a special case, and is much more of an issue in itself than the fact that it will also fragment files.

Those that deny this fact and say that ext3 needs to be defragmented fail at reading comprehension.

The fact that Ext3 fragments still remains. Over time you will eventually need to defragment your file system and at current there are no sufficient tools available to do so. 

Why continue to defend a file system which clearly has its flaws? If we don't criticize, issues like this will never be addressed.

---

### Post by hyper_ch on 2008-07-14
[http://www.tldp.org/LDP/sag/html/filesystems.html](http://www.tldp.org/LDP/sag/html/filesystems.html)

> 
Modern Linux filesystem keep fragmentation at a minimum by keeping all blocks in a file close together, even if they can't be stored in consecutive sectors. Some filesystems, like ext3, effectively allocate the free block that is nearest to other blocks in a file. Therefore it is not necessary to worry about fragmentation in a Linux system.


---

### Post by CatKiller on 2008-07-14
> **Jim! said:**
> The fact that Ext3 fragments still remains. Over time you will eventually need to defragment your file system and at current there are no sufficient tools available to do so. 

That doesn't follow. The filesystem becomes fragmented, but the files don't, so there is no need to defragment ext3 "over time". Who cares if /usr isn't stored physically close to /home? Performance is not affected. **tar** is perfectly sufficient for those times that you've done something to the filesystem that has fragmented the files.

> Why continue to defend a file system which clearly has its flaws? If we don't criticize, issues like this will never be addressed.

I'm not defending the filesystem, I'm correcting your misinformation. Nobody cares if you choose to use ext, Reiser, ZFS or whatever. There are other options if you don't like ext, but it is **not true** that general users will need to defragment their installs on ext.

There is no issue that needs to be criticised or addressed. There are situations where ext is not the appropriate choice, and for those situations other filesystems are available. If you are in the position that ext3 is not appropriate then you are already in the position to know that other options are available, since you'll already know that different filesystems are optimised for different things.

---

### Post by fyo on 2008-07-14
I strongly suspect the assumption that "ordinary users" don't fill their file systems (to within 15%) is false.

And if you are the type of user who fills their filesystem, you are likely going to have a hard time backing everything up to somewhere else and restoring it... for the simple reason that you're already out of disk space.

So, essentially, the only solution if you frequently get close to filling up your drive is to buy a new one.

In my opinion, it would be better if you had the option of clearing a bit of disk space and running a defragger.

---

### Post by CatKiller on 2008-07-14
> **fyo said:**
> So, essentially, the only solution if you frequently get close to filling up your drive is to buy a new one.

Surely this is necessarily true, regardless of any fragmentation issue? If you're running out of space on a regular basis, then your hard drive isn't big enough.

File fragmentation isn't really a big issue. I had some fragmentation for quite a long time after one of my users had filled /. It took so long to get round to sorting it out because it really didn't matter. If you get close to filling the partition, **some** of your files may get fragmented. With Windows filesystems, **all** of the files get fragemented, by design, even on a nearly empty partition. That's why many people are used to such a performance penalty with fragmentation. It really isn't anywhere near an issue with ext.

To clarify, ext3 does have flaws and areas that can be improved. But file fragmentation isn't one of them.

---

### Post by hidarikani on 2008-07-14
So many replies :o

I've learned that having 200 MB of free space most of the time (I do) is not OK and that ext3 is better than NTFS :)

---

### Post by fyo on 2008-07-14
> **CatKiller said:**
> File fragmentation isn't really a big issue.

...

To clarify, ext3 does have flaws and areas that can be improved. But file fragmentation isn't one of them.

Again, I challenge the validity of your assumptions - of which there appear to be two:

1) Users don't reach the point where they fragment their files.

2) Even if they do, it's not really a problem.

Before going any further it's worth stressing the following point:

**Who cares what some other file system does?**

We're talking ext3 here, nothing else. So let's keep everything within the context of ext3... i.e arguing "well, the performance drop isn't nearly as noticeable as in NTFS" should be dropped.

OK then...

Regarding point #1: In my personal experience, as a one-time administrator of > a thousand users, this assumption is blatantly incorrect. Users will fill their drives, no matter how large they are. Period. Not until they run out of disk space will they start deleting files, usually movies or other large media files. Granted, my experience was primarily with Windows users and it was a few years ago, but I submit that "ordinary Ubuntu users" likely exhibit similar behavior. This is not a question of "you should buy a new disk". That argument has nothing to do with anything.

Regarding point #2: The penalty for any given level of file fragmentation is (roughly) the same regardless of file system, so this reduces to the "there's just no (or much less) fragmentation with ext3" argument, i.e. essentially reverting to point #1.

A not uncommon usage case, one I've even subjected my own system two once or twice, is filling up your primary drive to within 5% (that's 15GB on a 300GB system) or even much less and then updating your system. The second part is the one that kills performance by causing important files to be fragmented.

Updating your system while low on disk space isn't the only scenario. Firefox and many other programs continually write to any number of files, where fragmentation can cause performance issues.

Let me give you two concrete examples from my own system:

```
$ sudo filefrag urlclassifier3.sqlite
urlclassifier3.sqlite: **761 extents found**, perfection would be 1 extent

$ sudo filefrag -v pak000.pk4
pak000.pk4: **566 extents found**, perfection would be 2 extents
```

These files are large, but not excessively so (50MB and 130MB, respectively).

Everything I've seen of "ordinary users" leads me to believe that running very close to the limit of one's disk space is the norm, not the exception.

There are many possible solutions to this problem, but the existence of a defragmenter would be quite helpful. Arrogant comments like "file fragmentation is not a problem with ext3"... not so much.

---

### Post by CatKiller on 2008-07-14
fyo, I pretty much agree with all of your points. It's just a question of emphasis.

Comparisons with other filesystems are valid. Otherwise there is no context. There are choices for which filesystem to use, and they all have strengths and weaknesses. The particular comparison to NTFS (or worse, FAT) is useful because there is a certain paranoia about file fragmentation for new users who are used to Windows, since there is such a performance hit. But, as you say, I think that point has now been adequately covered.

Your suggestion that installing a larger hard disk if a user is regularly running out of space has "nothing to do with anything" is clearly false on its face. If a user is regularly running out of space, then they need more. It's more-or-less axiomatic. If their usage pattern is such that they will only do housekeeping when their disk is full, then they are choosing to put themselves in the position where they need to upgrade. I agree with you that this is unlikely to change for those users.

I think you're right that the performance penalty may well be the same for a given level of file fragmentation, but the fact remains, which does tie in to your point 1, that this level of file fragmentation will be reached much more gradually with ext than with some other filesystems.

While it is possible to allocate an appropriate filesystem based on likely usage patterns for the relevant parts of the filesystem structure - for example different filesystems for /, /var and /home - and I note that this used to be the way it was always done, it seems unlikely that a user new to Linux would be at all comfortable selecting such an arrangement for themselves on first install. As it is, many users are coming across the concept of disk partitions for the very first time when they are installing Ubuntu. Hence the compromise of having a single ext3 filesystem mounted at / with a small tmpfs partition for swap.

The amount of file fragmentation that you'll get for a given amount of capacity usage is entirely dependent on the filesizes being used. This is not controversial. And you are correct that there are certain scenarios where files that are read often can become fragmented, which will give a performance penalty if they are too large to fit in the RAM cache. This is unfortunate.

I also agree with you that a defragmenter for ext3 would be useful. Currently the only dedicated defrag program for ext doesn't work with the journal of ext3, so the filesystem needs to first be converted to ext2. Which is obviously sub-optimal. But while a defragmenter for ext3 would indeed be "useful" it is not urgent, as far as I can tell. I suspect that before one appears, ext4 or some other filesystem will have become dominant and the desire for an online ext3 defragmenter will have become moot.

---

### Post by fyo on 2008-07-14
> **CatKiller said:**
> Comparisons with other filesystems are valid. Otherwise there is no context.

To play devil's advocate: The only context you need is optimal performance. I don't know exactly how much I'm suffering from the (quite significant) fragmentation of files on my system, but it doesn't really matter how much worse it would be for someone running Windows and NTFS. What matters is how much **I'm** affected and, just as importantly, what I can do about it.

> Your suggestion that installing a larger hard disk if a user is regularly running out of space has "nothing to do with anything" is clearly false on its face.

Although I think we probably agree to a large extent on this point (as well), I disagree with the assertion that it is false. You could stick a user with terabytes of disk space and they would use it up. The fundamental problem is that they treat it like a cache from which nothing is ejected until space runs out. It's not that they're actually USING the disk space. Much of it has been "used" and "forgotten", but since deleting stuff you're never going to use again takes time and effort, it's left until space runs low (or out).

You might argue that treating ones primary hard drive / partition like a cache is not a particularly good strategy, but I've never actually seen a user who didn't do this - although some, like my mother, never get close to running out of space because a few photos, even at 8 megapixels, don't take up a whole lot of space. With the increasing use of DVRs, high-def camcorders (and video from digital cameras), high-bandwidth Internet connections and high-capacity media disks (Blue-Ray), filling even a 1 terabyte "cache" isn't particularly demanding if nothing is ever ejected from it.

It's noteworthy that nothing is done to educate users about this. Neither Ubuntu nor any other Linux distrubtion I'm aware of warns users about the detrimental state of affairs they've subjected their system to... until they actually run out of disk space.

The real question might be "why care", but the answer there is simple. One of main selling points of Linux (when trying to persuade a casual user) is that it doesn't suffer from Windows Rot.

> While it is possible to allocate an appropriate filesystem based on likely usage patterns for the relevant parts of the filesystem structure - for example different filesystems for /, /var and /home - and I note that this used to be the way it was always done, it seems unlikely that a user new to Linux would be at all comfortable selecting such an arrangement for themselves on first install.

I think you hit the nail on the head there. A "media" partition would solve many of the problems (or an application partition). I don't think it HAS to be daunting for the average user - it just has to be hidden from them ;-). Since the partitions are going to be automounted anyway, they could simply be looked at as "folders". Ahhh, well, I guess it's not in the Linux philosophy to deceive... nay... abstract away... the truth.

> And you are correct that there are certain scenarios where files that are read often can become fragmented, which will give a performance penalty if they are too large to fit in the RAM cache. This is unfortunate.

Your use of "certain scenarios" makes it sound like something that doesn't happen often "in the real world". I would argue the contrary - that those "certain scenarios" are the norm, rather than the exceptions.

And files don't have to be larger than the RAM cache to affect performance. That's not even the main impact of fragmentation. Rather, it generally increases system "sluggishness" by increasing load times. Naturally, in some cases this increase (along with the rest of the load time) could be completely masked by proper caching. Unfortunately, most applications on Linux don't do decent caching (read ahead / guessing etc). It's simply not in the spirit of "server optimization", which is (sadly) how Linux is optimized.

A good example is something as simple as an image viewer. None of the standard image viewers on Ubuntu do read ahead caching of images. And if your 563kB image is fragmented in 47 parts (a real example of an image I downloaded last night), that certainly affects performance.

In conclusion:

- Fragmentation is a real problem on ext3, much more so than most acknowledge.
- Nothing is done to advise or educate users about preventing fragmentation, which is a shame because (unlike NTFS) simple measures will all but eliminate the problem.
- No tools exist (in the main repositories) to rectify the problems once they occur.
- Applications are not optimized to minimize the effects of fragmentation.

---

### Post by VMC on 2008-07-14
> Although I think we probably agree to a large extent on this point (as well), I disagree with the assertion that it is false. You could stick a user with terabytes of disk space and they would use it up. The fundamental problem is that they treat it like a cache from which ***nothing is ejected until space runs out***. It's not that they're actually USING the disk space. Much of it has been "used" and "forgotten", but since deleting stuff you're never going to use again takes time and effort, it's left until space runs low (or out).

Something like the goldfish scenario. Put a goldfish in a larger bowl and it will grow accordingly. I find the above statement a true  assumption. I like to keep stuff off that I no longer use. Like video. That's one that keeps growing. If I can't burn it to dvd disk  , I usually delete it.

---

### Post by markbuntu on 2008-07-14
That's why we have terabyte hard drives.:)

---

### Post by fyo on 2008-07-14
Something's odd with the ext3 algorithm... I just copied some photos around on my drive and the final copies were much less fragmented than the originals, however... they were all still fragmented (2 fragments each, except for one at 10 fragments and one at 43 - both files < 1MB). Sure, I don't have a lot of free space, but I do have many GIGS of it. Don't tell me I don't have 600kB free contiguous space in there somewhere...

---

### Post by articpenguin on 2008-07-14
> **fyo said:**
> Something's odd with the ext3 algorithm... I just copied some photos around on my drive and the final copies were much less fragmented than the originals, however... they were all still fragmented (2 fragments each, except for one at 10 fragments and one at 43 - both files < 1MB). Sure, I don't have a lot of free space, but I do have many GIGS of it. Don't tell me I don't have 600kB free contiguous space in there somewhere...

heres the truth

The Linux File allocator sucks. The Kernel VFS breaks each file into 4KB chunks this means the Filesystem will only allocate 4KB chunks of data per I/O. JFS is a good example of this. 

from [http://osdir.com/ml/file-systems.jfs.general/2007-02/msg00000.html](http://osdir.com/ml/file-systems.jfs.general/2007-02/msg00000.html)

So it's not that jfs couldn't find 3 contiguous blocks, but that it
really doesn't look for them.  It's allocating one block at a time, and
will grow into contiguous space if it can. 

ext3 lacks mutiple block allocation too. I dont know about reiserfs or xfs but there is a good chance they suffer from this too.


At least NTFS knows ahead of time when copying a file and it will allocate single extent for the exact file size.

---

### Post by articpenguin on 2008-07-14
also the max extent size of ext3 can only be 128MB by the way ext3 breaks the filesystem up.

---

### Post by Redrazor39 on 2008-07-14
I know you started a huge discussion here for a simple question but all you need to know is this:

You don't need to worry about defragmentation. Your system won't slow down or screw up like a fragmented Windows install.

---

### Post by articpenguin on 2008-07-14
I really do think NTFS is more resistant to fragmentation than ext3.


I downloaded an ubuntu iso torrent.

on ntfs the File ended up in 2018 fragments.

On ext3 it ended up on 14428 fragments

---

### Post by knutschr on 2008-07-15
Could you move both files to another directory, then move them back and tell what defragmentation you find now?

---

### Post by fyo on 2008-07-15
> **articpenguin said:**
> I really do think NTFS is more resistant to fragmentation than ext3.


I downloaded an ubuntu iso torrent.

on ntfs the File ended up in 2018 fragments.

On ext3 it ended up on 14428 fragments

That's a really, really bad "test" for so many reason, I don't even know where to start.

To even get close to being able to compare the two, you would need to make sure that the initial state of the partition was the same. That is, that the used space was located in the same areas of the disk and that a similar amount of free space was available.

You would also need to ensure that your download (or copy) program worked the same way. Does it reserve all the space initially in one big chuck? Does it use sparse files? (I love sparse files, but they will result in more fragmentation). The worst case for NTFS is "streaming" data. I was unable to use my Firewire camcorder with WinXP/NTFS at one point because free space was so fragmented and NTFS allocated from beginning to end of drive, regardless of free chunks. The slow-down was so severe that frames were lost.

Anyway, I don't think anyone who has seriously compared usage of NTFS and ext3 can sanely argue that NTFS is more resistant to fragmentation. With any two different file system implementations, you can ALWAYS find a case where one is better / faster / whatever than the other. In general, however, there is no question that NTFS suffers *much* more from fragmentation than ext3.

---

### Post by fyo on 2008-07-15
> **articpenguin said:**
> 
ext3 lacks mutiple block allocation too.

That is incorrect. Ext3 has had multiple block allocation since kernel 2.6.17 (about two years ago):

[http://www.sfr-fresh.com/linux/v2.6/ChangeLog-2.6.17](http://www.sfr-fresh.com/linux/v2.6/ChangeLog-2.6.17)

Btw, please make it clear when you are quoting other sources and when you are expressing your own opinion.

---

### Post by knutschr on 2008-07-15
> **fyo said:**
> 
You would also need to ensure that your download (or copy) program worked the same way. Does it reserve all the space initially in one big chuck? Does it use sparse files? (I love sparse files, but they will result in more fragmentation). The worst case for NTFS is "streaming" data. 

It seems from arcticpenguin's results that streaming data is worst case for ext3 too.
Ext3 does not know the size of the file, and fill in empty small places, like NTFS.
I think if he moves the file, ext3 will find a place big enough for the file. NTFS will not care, I think.

It will be very interresting to see his results.

Anyway: Good to know that this can happen by downloading files.(As I said: Ext3 will 'repair' it by moving it, I think)

---

### Post by fyo on 2008-07-15
> **knutschr said:**
> It seems from arcticpenguin's results that streaming data is worst case for ext3 too.
Ext3 does not know the size of the file, and fill in empty small places, like NTFS.

Sounds to me like articpenguin is basing his statements on ext3 as it was in version 2.4 of the Linux kernel.

Streaming is always difficult, since the file system has no way of knowing what the final file size will be.

However, ext3 allocates blocks in MEMORY first, which are then written back to disk once the window is full or file closed. This results in a stream being much less fragmented than NTFS, which just "dumbly" writes from first-free-block, regardless of resulting fragmentation.

This also overcomes the "4kB chunks" issue he quotes someone on (with a link, but without indicating that he is quoting) for the jfs file system.

Here's nice paper on the state of ext3 development by developers from IBM:

[http://ext2.sourceforge.net/2005-ols/paper-html/cao.html](http://ext2.sourceforge.net/2005-ols/paper-html/cao.html)

Perhaps more accessible (easier and shorter) is this set of "slides" from a presentation (by the same guys) essentially covering the same (but much lighter on the details):

[http://ext2.sourceforge.net/2005-ols/2005-ols-ext3-presentation.pdf](http://ext2.sourceforge.net/2005-ols/2005-ols-ext3-presentation.pdf)

EDIT: Note that the paper and associated presentation are some 3 years old. Further developments have been made since then.

---

### Post by fyo on 2008-07-15
> **articpenguin said:**
> also the max extent size of ext3 can only be 128MB by the way ext3 breaks the filesystem up.

In Ext3 it's a "big block group" not an extent, which isn't supported (mainstream, anyway, there's a binary incompatible patch to add extent support). Extents are actually more efficient, so the distinction is not irrelevant.

Microsoft's own "best practices" recommendation for NTFS is that defragmentation in clusters (extents) of 64MB is the optimal balance of overhead vs performance.

There are real things you can do with NTFS (and ext3) to minimize fragmentation, but since not many people use low-level API calls to write to disk, the only thing that matters is actual usage in common applications. For example, if files in Windows were always pre-allocated in full and files extended 64MB at a time (or corresponding multiple of volume cluster size), fragmentation would be minimal. Unfortunately, the NTFS cluster allocation algorithm is undocumented and repeatability is very low, likely due to the inner workings of the Windows Cache Manager.

---

### Post by knutschr on 2008-07-15
Strange thing, this...
I have 2 GB RAM, and latest kernel.
I downloaded latest Ubuntu iso, and it gave 273 extents.
Then I copied it to another directory. That took some seconds.

I then examined the copied file:
> knut@knut:~/Program$ sudo filefrag ubuntu-8.04.1-desktop-i386.iso
ubuntu-8.04.1-desktop-i386.iso: 175 extents found, perfection would be 6 extents


This is not what I had hoped for :-(

Well. This may be is peanuts. One can never see anything from some hundred extents in a GB file, though!

(If anyone don't have filefrag installed: It is in the package e2fsprogs)

---

### Post by fyo on 2008-07-15
How much free space do you have? (Absolute and as a percentage)

Getting even close to the limit will severely impact performance, for reasons I don't quite understand.

---

### Post by knutschr on 2008-07-15
:eek:
That explains it!

> knut@knut:~/Program$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             142G  133G  1,6G  99% /
varrun               1008M  156K 1008M   1% /var/run
varlock              1008M     0 1008M   0% /var/lock
procbususb           1008M   68K 1008M   1% /proc/bus/usb
udev                 1008M   68K 1008M   1% /dev
devshm               1008M  2,5M 1005M   1% /dev/shm
lrm                  1008M   40M  969M   4% /lib/modules/2.6.24-19-rt/volatile

Haven't looked at this for a while!

Impressive that a file of 1 GB didn't get more defragmented!

---

### Post by fyo on 2008-07-15
Dupe, sorry

---

### Post by knutschr on 2008-07-15
Yes, stupid to test fragmentation of a large file as this with 1% free space :-)

I emtied my Trash and then had
> knut@knut:~/Program$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             142G  107G   27G  80% /
varrun               1008M  156K 1008M   1% /var/run
varlock              1008M     0 1008M   0% /var/lock
procbususb           1008M   68K 1008M   1% /proc/bus/usb
udev                 1008M   68K 1008M   1% /dev
devshm               1008M  2,5M 1005M   1% /dev/shm
lrm                  1008M   40M  969M   4% /lib/modules/2.6.24-19-rt/volatile


Then I downloaded the Ubuntu iso again, and got:
> knut@knut:~/Program$ sudo filefrag /home/knut/downloads/ubuntu-8.04.1-desktop-i386.iso
/home/knut/downloads/ubuntu-8.04.1-desktop-i386.iso: 438 extents found, perfection would be 6 extents


I get the same result after moving it or copying it.
Still. This is a very little fragmentation.

I have also looked at some programs in /usr/bin and they all are like this:
> knut@knut:/usr/bin$ sudo filefrag firefox
firefox: 1 extent found


And these are often used programs!

---

### Post by VMC on 2008-07-15
I've never used 'filefag' before. Just curious because of your concern of extents, I also checked '/usr/bin' just to see myself. I had 49 files over 1 extent. The largest was 31 extents. What can I do to remedy this. Or is this just a "Red Herring" and not worth the paper it's written on?

```
[SIZE="3"]/usr/bin/dbus-daemon: 10 extents found, perfection would be 1 extent
/usr/bin/directomatic: 15 extents found, perfection would be 1 extent
/usr/bin/dpkg: 11 extents found, perfection would be 1 extent
/usr/bin/foomatic-rip: 15 extents found, perfection would be 1 extent
/usr/bin/gdb: 22 extents found, perfection would be 1 extent
/usr/bin/gdbtui: 23 extents found, perfection would be 1 extent
/usr/bin/gedit: 11 extents found, perfection would be 1 extent
/usr/bin/gnome-help: 19 extents found, perfection would be 1 extent
/usr/bin/gnome-text-editor: 11 extents found, perfection would be 1 extent
/usr/bin/iasl: 34 extents found, perfection would be 1 extent
/usr/bin/k9copy: 19 extents found, perfection would be 1 extent
/usr/bin/mattrib: 10 extents found, perfection would be 1 extent
/usr/bin/mbadblocks: 10 extents found, perfection would be 1 extent
/usr/bin/mcat: 10 extents found, perfection would be 1 extent
/usr/bin/mcd: 10 extents found, perfection would be 1 extent
/usr/bin/mclasserase: 10 extents found, perfection would be 1 extent
/usr/bin/mcopy: 10 extents found, perfection would be 1 extent
/usr/bin/mdel: 10 extents found, perfection would be 1 extent
/usr/bin/mdeltree: 10 extents found, perfection would be 1 extent
/usr/bin/mdir: 10 extents found, perfection would be 1 extent
/usr/bin/mdu: 10 extents found, perfection would be 1 extent
/usr/bin/mencoder: 67 extents found, perfection would be 1 extent
/usr/bin/mformat: 10 extents found, perfection would be 1 extent
/usr/bin/minfo: 10 extents found, perfection would be 1 extent
/usr/bin/mlabel: 10 extents found, perfection would be 1 extent
/usr/bin/mmd: 10 extents found, perfection would be 1 extent
/usr/bin/mmount: 10 extents found, perfection would be 1 extent
/usr/bin/mmove: 10 extents found, perfection would be 1 extent
/usr/bin/mpartition: 10 extents found, perfection would be 1 extent
/usr/bin/mrd: 10 extents found, perfection would be 1 extent
/usr/bin/mren: 10 extents found, perfection would be 1 extent
/usr/bin/mshowfat: 10 extents found, perfection would be 1 extent
/usr/bin/mtools: 10 extents found, perfection would be 1 extent
/usr/bin/mtoolstest: 10 extents found, perfection would be 1 extent
/usr/bin/mtype: 10 extents found, perfection would be 1 extent
/usr/bin/mzip: 10 extents found, perfection would be 1 extent
/usr/bin/nautilus: 18 extents found, perfection would be 1 extent
/usr/bin/nautilus-connect-server: 10 extents found, perfection would be 1 extent
/usr/bin/net: 13 extents found, perfection would be 1 extent
/usr/bin/ntlm_auth: 31 extents found, perfection would be 1 extent
/usr/bin/pidgin: 20 extents found, perfection would be 1 extent
/usr/bin/skype: 19 extents found, perfection would be 1 extent
/usr/bin/smbcacls: 21 extents found, perfection would be 1 extent
/usr/bin/smbcquotas: 11 extents found, perfection would be 1 extent
/usr/bin/smbspool: 12 extents found, perfection would be 1 extent
/usr/bin/smbtree: 20 extents found, perfection would be 1 extent
/usr/bin/vamps: 11 extents found, perfection would be 1 extent
/usr/bin/wbinfo: 12 extents found, perfection would be 1 extent
/usr/bin/yelp: 19 extents found, perfection would be 1 extent[/SIZE]

```

---

### Post by CatKiller on 2008-07-15
> **articpenguin said:**
> I downloaded an ubuntu iso torrent.

Fragmentation by BitTorrent clients is a known issue and is not related to ext, as such. As you are aware, BitTorrent works by breaking a file into many many chunks so that you can get the file concurrently from many sources. Since each chunk gets written to disk independently of all the others rather than as a single file, the file will be very fragmented when the download is complete.

It might be possible to have a consolidation step that moved all the chunks together at the end of the download, but most users would not see the point of the files they've just downloaded being suddenly inaccessible and unable to be seeded for a short period of time.

---

### Post by CatKiller on 2008-07-15
> **fyo said:**
> To play devil's advocate: The only context you need is optimal performance. I don't know exactly how much I'm suffering from the (quite significant) fragmentation of files on my system, but it doesn't really matter how much worse it would be for someone running Windows and NTFS. What matters is how much **I'm** affected and, just as importantly, what I can do about it.

Well, one of the things that you could do is use a different filesystem ;)

> It's noteworthy that nothing is done to educate users about this. Neither Ubuntu nor any other Linux distrubtion I'm aware of warns users about the detrimental state of affairs they've subjected their system to... until they actually run out of disk space.

That is an interesting point. There are configurable notification points for warning of partition capacity usage, but they only really inform of the fact, and make no mention of the consequences. It would probably be nice to have a warning at, say, 75% full that explained that performance may suffer, with links to further information about how. Currently, though, I'm not sure what advice would be given other than to free up more space.

Perhaps if there were some pervasive backup solution included in all installations - something along the lines of Apple's Time Machine, I guess - there might be the option of replacing fragmented files with their non-fragmented brethren. Defragmentation and backup have gone hand-in-hand for so long that to continue in that vein might provide a really powerful tool.

> The real question might be "why care", but the answer there is simple. One of main selling points of Linux (when trying to persuade a casual user) is that it doesn't suffer from Windows Rot.

Actually, I've never mentioned this. Most people that I might mention Linux to wouldn't really notice that the performance of their computer has degraded over time. I think that I only really mention (in varying order, dependant on the audience)

[LIST=1]
[*]It is Free (capital Free)
[*]Software installation and update are actually sensible
[*]User privileges are actually sensible
[*]It is free (lower-case free) and can be sampled for zero investment
[*]There are no viruses in the wild
[*]Compiz :)
[/LIST]

> I think you hit the nail on the head there. A "media" partition would solve many of the problems (or an application partition). I don't think it HAS to be daunting for the average user - it just has to be hidden from them ;-). Since the partitions are going to be automounted anyway, they could simply be looked at as "folders". Ahhh, well, I guess it's not in the Linux philosophy to deceive... nay... abstract away... the truth

Whilst it would be difficult to second-guess every scenario enough to provide a more sensible one-size-fits-all configuration, and insisting on full configuration for all users would likely scare many away, it might be possible to have an intermediary step with some common usage patterns. A large-ish / (or /usr, maybe?) partition would be necessary, so that users were free to experiment with many packages without care, and separate /home/whatever partitions that took up most of the rest of the drive, with possible /boot, /var, /whatever assigned based on the profile. As it is, we're getting Documents and Photos directories in the Home folder, so there isn't really any reason why these couldn't be mount points for other filesystems.

While it is not in the Free philosophy to make anything that cannot be changed, there is a longstanding tradition from UNIX to have many options but sensible defaults. Information can be provided to the interested. Plus Gnome, rightly or wrongly, has a reputation for making the first line of configuration "simple". So this kind of approach would not necessarily be out of place.

> Your use of "certain scenarios" makes it sound like something that doesn't happen often "in the real world". I would argue the contrary - that those "certain scenarios" are the norm, rather than the exceptions.

Well, I did say that we mostly differ on emphasis. I feel that it's only an issue on edge cases, and you feel that it is an issue in more general terms. I've still enjoyed this discussion immensely, though.

> And files don't have to be larger than the RAM cache to affect performance. That's not even the main impact of fragmentation. Rather, it generally increases system "sluggishness" by increasing load times. Naturally, in some cases this increase (along with the rest of the load time) could be completely masked by proper caching. Unfortunately, most applications on Linux don't do decent caching (read ahead / guessing etc). It's simply not in the spirit of "server optimization", which is (sadly) how Linux is optimized.

The compromise between longer load times and slower running performance is an open question. It is safe to say that developers differ on the approaches that they take for aggressively optimising one over the other. And the server heritage has certainly influenced the choices that have been made. In a world of continual uptime, a longer load time is a penalty that only has to be paid once, whereas if the environment is restarted often it becomes much more expensive. Perhaps the influx of a new constituency will cause different choices to be made in the future.

> A good example is something as simple as an image viewer. None of the standard image viewers on Ubuntu do read ahead caching of images. And if your 563kB image is fragmented in 47 parts (a real example of an image I downloaded last night), that certainly affects performance.

In conclusion:

- Fragmentation is a real problem on ext3, much more so than most acknowledge.
- Nothing is done to advise or educate users about preventing fragmentation, which is a shame because (unlike NTFS) simple measures will all but eliminate the problem.
- No tools exist (in the main repositories) to rectify the problems once they occur.
- Applications are not optimized to minimize the effects of fragmentation.

---

### Post by articpenguin on 2008-07-15
I just created a swap file on a relativie empty harddrive (97% free space) around 153GB free. On ext3 i created the same file 3 times

512Mb.swap: 440 extents found, perfection would be 5 extents

512Mb.swap: 216 extents found, perfection would be 5 extents

512Mb.swap: 352 extents found, perfection would be 5 extents


So I strongly think ext3 is still allocating 4KB at a time.

---

### Post by Checkhovian on 2008-07-17
Does Linux need to be defragmented? If so, how?

---

### Post by dracayr on 2008-07-17
no, it's not necessary. You also don't need any antivirus programs

dracayr

---

### Post by ivze on 2008-07-17
As far as i know, there is no standart way to defrag ext3 filesystem.
Whether or not it is necessary is a controversial question.
The standart defragmenter will be in ext4, being developed.

---

### Post by fiddledd on 2008-07-17
> **Checkhovian said:**
> Does Linux need to be defragmented? If so, how?

Here is an old link with an explanation, and with diagrams :)

[http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting](http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting)

---

### Post by space.duck on 2008-07-17
hardy forces a HD check every 30 boots.
:)

---

### Post by philinux on 2008-07-17
As always there isn't really a yes/no answer.

[http://www.itworld.com/nls_unixfrag040929](http://www.itworld.com/nls_unixfrag040929)

Have a google around you'll find lots of articles.

---

### Post by philinux on 2008-07-17
As always there isn't really a yes/no answer. Just more questions.

[http://www.itworld.com/nls_unixfrag040929](http://www.itworld.com/nls_unixfrag040929)
[http://en.wikipedia.org/wiki/Ext3](http://en.wikipedia.org/wiki/Ext3)
Have a google around you'll find lots of articles.

---

### Post by bodhi.zazen on 2008-07-17
This thread seems to be going nowhere -> recurring discussions.

---

### Post by ryniek on 2008-07-17
[Here]("http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting") You have answer for Your qestion. :)

---

### Post by stchman on 2008-07-17
> **Checkhovian said:**
> Does Linux need to be defragmented? If so, how?

The EXT3 filesystem does not require defragging like FAT32 or NTFS.  If you have an NTFS partition you mount then it still requires defragging.

---

### Post by oldos2er on 2008-07-17
> **space.duck said:**
> hardy forces a HD check every 30 boots.
:)

 fsck does not equal defrag.

---

### Post by SunnyRabbiera on 2008-07-17
> **oldos2er said:**
> fsck does not equal defrag.

true but it checks the FS integrity nonetheless.
But no, there is no need to defrag with ext3

---

### Post by todlangweilig on 2008-07-17
I think there was a thread about this 3 days ago
[http://ubuntuforums.org/showthread.php?t=858925](http://ubuntuforums.org/showthread.php?t=858925)

---

### Post by bapoumba on 2008-07-18
Threads merged.

---

### Post by Canis familiaris on 2008-07-19
Ext3 as such does not require defragmentation.
I dunno whether the filesystem fragments or not, but I have never experienced any slowdowns.

About people arguing ext3 getting fragmented when filled up, I would like to say that NTFS fragments far too more.
But if you say NTFS at least has Defragmenting tools, I would say that when space is filled up to that extent, Windows defragger doesnt work. It needs certain amt. of free space.

---

### Post by Erunno on 2008-07-19
ext3 suffers from fragmentation like any other filesystem. There is no magic algorithm which will avoid fragmentation under all possible (especially high) I/O loads. So over time fragmentation increases on an ext3 partition. That's why ext4 will implement some anti-fragmentation strategies already found in other filesystems like XFS (e.g. delayed allocation, extents, etc.). Plus, it will feature an online defragmentation tool like Windows. The myth that ext3 doesn't cause fragmentation probably came up to cover up the deficiencies in ext3. After all, if Linux doesn't have a feature it doesn't need it. :roll:

---

### Post by hyper_ch on 2008-07-19
well, I still stick to what the TLDP say - hence no defrag tool needed.

---

### Post by articpenguin on 2008-07-19
I cant wait for ext4:). 

BTY ext3 fragmentation is not as bad as ntfs fragmentation. Ext3 stores the block locations in the files inode. NTFS stores it in other MFT records.

---

