---
title: "Why don't they fix NTFS?"
date: 2010-12-23
forum: Programming Talk
---

### Post by fela on 2010-12-23
(This might not be the appropriate forum, but here goes)

My question is about fragmentation.

The way I see it (tell me if I'm wrong!), fragmentation occurs on NTFS because files are put as near to the beginning of the disk as possible (so if I had one file and I added another one, it would start straight from the next block along from the end of the last file). Obviously this causes fragmentation when files are modified.

And the way I see it, the cure to this is to put files in random locations on disk when they are created.

Seeing as these two points seem pretty obvious (especially if you are an OS programmer :D), why has MS still not fixed NTFS?

---

### Post by worksofcraft on 2010-12-23
> **fela said:**
> (This might not be the appropriate forum, but here goes)

My question is about fragmentation.

The way I see it (tell me if I'm wrong!), fragmentation occurs on NTFS because files are put as near to the beginning of the disk as possible (so if I had one file and I added another one, it would start straight from the next block along from the end of the last file). Obviously this causes fragmentation when files are modified.

And the way I see it, the cure to this is to put files in random locations on disk when they are created.

Seeing as these two points seem pretty obvious (especially if you are an OS programmer :D), why has MS still not fixed NTFS?

The idea of NTFS is to get better performance by minimizing disk head movements. Thus Microsoft likes to lump everything together and not only that but they don't store all the index in one place like they used to with FAT: Instead they distribute chunks of it throughout the disk. They even allocate the tracks in alternating ascending/descending order so that it cuts down on head movements from the allocation table blocks to the data blocks...

The problem I see with the Microsoft design is that they don't differentiate between read only protected parts of the file system (which rarely change and can be nicely defragmented as sequentially organized executable programs)...  and your working documents that are being modified all the time and quite likely do get scattered in all directions. OTOH I'm not convinced that is an issue with NTFS but more of their file system hierarchy.

---

### Post by trent.josephsen on 2010-12-23
Lots of files don't ever have to be modified.  You can't know on the filesystem level what the usage pattern of a file will be at its creation.

Also, placing them in random locations would work for fast, sparse drives, but the disk would have to do a lot more work when loading several files that would otherwise be sequential.  Furthermore, when the drive started getting full, you would end up with lots of very small gaps.  The performance drop would probably be quite sudden; you'd have "good" performance on the first 60% of the files on the drive at the cost of absolutely horrible performance on the last 40%.

But that's rather tangential to the question.  Let me ask you something.  What good would it do Microsoft to "fix" NTFS?

---

### Post by fela on 2010-12-23
> **trent.josephsen said:**
> But that's rather tangential to the question.  Let me ask you something.  What good would it do Microsoft to "fix" NTFS?

Better customer relations ;)

Another thought I just had in terms of differences between Windows and Linux is that Windows *only* natively supports NTFS. Let's not go into all the ones Linux supports, but suffice to say that if *you* have an idea of the usage pattern of a Linux system before you install it, you can pick and choose whichever file system is best for the job. Obviously this is a different issue, and is one of the main advantages of Linux over Windows I guess.

> The performance drop would probably be quite sudden; you'd have "good" performance on the first 60% of the files on the drive at the cost of absolutely horrible performance on the last 40%.

So is this how ext[2,3,4] work?

> The idea of NTFS is to get better performance by minimizing disk head movements.

So you're saying fragmentation causes less head movements than scattered but sequential (in and of themselves) files? I would have thought that this is only true in an instance where you're accessing many small files.

In fact, my (Linux) server's disk (ext3) is almost 80% full, and it seems to still do a fine job of random access (web server with quite a few websites), but TBH there isn't really any application on it which requires high raw throughput.

I often notice my Windows desktop turn into a new PC every time it gets defragged. Maybe my usage patterns are not what MS intended them to be :p

---

### Post by t1497f35 on 2010-12-23
The file-system is not something an average desktop user can judge upon, nor will he know it's the file-system to blame when certain issues arise, so Microsoft is only trying to make it good enough, which it is, at least compared to FAT32 which they dropped completely from the latest XP versions and the newer vista/7.
There are scenarios where NTFS looks like a slightly better approach, which is really a trade-off. For instance if you've used the drive a little and you wanna create a new partition chances are good you won't have to move files around because it doesn't tend to scatter files around the whole partition like ext3/4. In other scenarios this approach proves worse, so it's really a matter of taste/trade-off.
No question, to me Btrfs would be way better since it's not that much slower than ext3 (sometimes faster) but it provides quite a lot of safety, though the "safety" is probably not proven yet. It also has a lot of features I would probably wanna play around with.

---

### Post by fela on 2010-12-23
> **t1497f35 said:**
> The file-system is not something an average desktop user can judge upon, nor will he know it's the file-system to blame when certain issues arise, so Microsoft is only trying to make it good enough, which it is, at least compared to FAT32 which they dropped completely from the latest XP versions and the newer vista/7.

Hmm, seems like that's the story with alot of MS stuff.

I wonder how people manage with Microsoft based servers? Cause with a server, you really do need to optimize for the situation...

---

### Post by psusi on 2010-12-23
Microsoft has been cranking out operating systems using the same brain dead allocation algorithm for 30 years.  They don't seem to change either because they are retarded, or because their sheep like users happily accept the fact that they regularly have to defrag.  Linux has been spreading files around to avoid fragmentation for 20 years now, which is why you don't need to defrag.

---

### Post by trent.josephsen on 2010-12-23
> **fela said:**
> So is this how ext[2,3,4] work?
[Apparently](http://en.wikipedia.org/wiki/Ext2#Allocating_Data), those filesystems cluster data according to its location in the hierarchy.  It's more of a middle ground between completely arbitrary placement and completely sequential placement.

Ideally, of course, all your files would be laid out sequentially and contiguously, but <understatement>rebuilding half the filesystem every time you write to it would be a pretty significant performance hit.</understatement>  So we compromise.  NTFS does pretty well, for the first few months or so.  ext3 seems to do a much better job in the long term, at least for my usage pattern.  They represent different balances between the two basic allocation algorithms.

Eventually I hope SSDs will solve these problems for us.  They need to get cheaper, though, first...

---

### Post by 3Miro on 2010-12-23
The goal of MS is not to make a good Operating System. The goal of MS is to sell and OS and there is a big difference. Sometimes those overlap, but often they don't. If you cannot market a feature, then it will bring no cash, so why bother.

FOSS on the other hand has a different philosophy. People that volunteer to make Linux don't care if they can sell it to other people (Canonical and RedHat care, but most of the volunteer developers don't). People that volunteer usually want to make a good system for themselves.

---

### Post by worksofcraft on 2010-12-23
> **fela said:**
> 
So you're saying fragmentation causes less head movements than scattered but sequential (in and of themselves) files?
...

I often notice my Windows desktop turn into a new PC every time it gets defragged. Maybe my usage patterns are not what MS intended them to be :p

Nope not what I'm saying... I'm just quoting what I read about Microsoft's explanation for why they designed NTFS to work the way it does. Apparently they recruited a specialist team of world renowned experts and I presume they did some genuine studies and research.

I suspect their design focussed on technical issues, but you can't expect any file system to be psychic and know how you are going to use each file as you create it.

If you fit a second disk drive, you might be able to install and defrag all the static sequential system files and applications  on one and put all your scattered and randomly accessed documents  on the other and hopefully you will find your system performance doesn't degrade quite as rapidly!?

---

### Post by psusi on 2010-12-23
> **worksofcraft said:**
> Nope not what I'm saying... I'm just quoting what I read about Microsoft's explanation for why they designed NTFS to work the way it does. Apparently they recruited a specialist team of world renowned experts and I presume they did some genuine studies and research.

I suspect their design focussed on technical issues, but you can't expect any file system to be psychic and know how you are going to use each file as you create it.

If you fit a second disk drive, you might be able to install and defrag all the static sequential system files and applications  on one and put all your scattered and randomly accessed documents  on the other and hopefully you will find your system performance doesn't degrade quite as rapidly!?

You are mixing up the design layout of the fs with fragmentation.  They chose a decent layout when designing the fs, but when it came time to write the driver, they did a poor job.

More specifically, they spread the allocation bitmaps around throughout the disk rather than all at the start in order to reduce seeks, but that has nothing to do with how they allocate data blocks to files.

---

### Post by worksofcraft on 2010-12-23
> **psusi said:**
> You are mixing up the design layout of the fs with fragmentation.  They chose a decent layout when designing the fs, but when it came time to write the driver, they did a poor job.

More specifically, they spread the allocation bitmaps around throughout the disk rather than all at the start in order to reduce seeks, but that has nothing to do with how they allocate data blocks to files.

Yep that's why I said on post #2
> OTOH I'm not convinced that is an issue with NTFS but more of their file system hierarchy.

---

### Post by psusi on 2010-12-23
> **worksofcraft said:**
> Yep that's why I said on post #2

Filesystem hierarchy is the placement of files within directories, not where they are stored on the disk.

For example, the core windows files are in \windows\system32, and add on programs are in \program files, etc.

---

### Post by worksofcraft on 2010-12-23
> **psusi said:**
> Filesystem hierarchy is the placement of files within directories, not where they are stored on the disk.

For example, the core windows files are in \windows\system32, and add on programs are in \program files, etc.

... does "core windows files" then make a distinction between ones that are regularly being updated and ones that are installed and then just opened for read/execute?

---

### Post by fela on 2010-12-24
I think the issue here is that Windows doesn't allow for a choice of which FS to use.

I mean, with Linux not only do you have a choice of myriad filesystems but you can even store your home directory, binaries, shared libraries, configuration files and blah-de-blah wherever you want :D

---

### Post by Dark_Stang on 2010-12-24
I wonder how much money is wasted each year because of defragging. I bet it's in the billions of USD. There should be a class action lawsuite over it.

---

### Post by Reiger on 2010-12-24
Actually, Microsoft allows you to use whatever filesystem you like: they just don't distribute any drivers other than those they made themselves. I think the exception would be booting the kernel, though, that does require MS' own fs. For instance if you want to, you can grab an ext2/3 driver from: [http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by fela on 2010-12-25
> **Reiger said:**
> Actually, Microsoft allows you to use whatever filesystem you like: they just don't distribute any drivers other than those they made themselves. I think the exception would be booting the kernel, though, that does require MS' own fs. For instance if you want to, you can grab an ext2/3 driver from: [http://www.fs-driver.org/](http://www.fs-driver.org/)

What about ext4, xfs, etc...

---

### Post by Reiger on 2010-12-25
They don't write the drivers, you're free to port them. That ext2/ext3 driver isn't made by MS either. You do realise that your post is awfully similar to complaining that Microsoft Office doesn't work on Linux out of the box, right?

---

### Post by fela on 2010-12-25
> **Reiger said:**
> They don't write them, you're free to port them. You do realise that your post is awfully similar to complaining that Microsoft Office doesn't work on Linux out of the box...

I think if you write an OS you should have the decency to write a decent FS for it...

And does Windows support custom FSes for its system partition?

---

