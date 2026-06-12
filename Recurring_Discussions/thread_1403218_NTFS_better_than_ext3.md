---
title: "NTFS better than ext3?"
date: 2010-02-10
forum: Recurring Discussions
---

### Post by Udayakiran on 2010-02-10
I know i could be lynched for this, but anyway, is NTFS better than ext3?

I have been using NTFS for about 8-10 years, and never have I lost any data on a NTFS partition. I live in a country where blackouts and brownouts are commonplace. In spite of the frequent power cuts, there has never been data corruption on NTFS. File fragmentation, sure, but no data corruption. 

I've set up a media-server cum torrent-box in a bare bones headless system using Ubuntu server 9.10. And every time after a power failure, I'm having to do a file system check. Thankfully, due to ext3's journalling system, the data is always recovered. But why does it happen? It never happens with NTFS.

So my question is, is NTFS better than ext3?

---

### Post by juancarlospaco on 2010-02-10
no.

---

### Post by Kenny_Strawn on 2010-02-10
> **juancarlospaco said:**
> no.

Absolutely not. NTFS does not have a journal, neither is it 64 bit like Ext4.

Note: Ext4 is 64 bit. Ext3 isn't. However, Microsoft does have a 64 bit operating system. What they don't have is a 64 bit FS.

---

### Post by oldsoundguy on 2010-02-10
No .. NTFS allows excessive fragmentation of files in it's management of files.  ext3-4 does NOT.
Not needed to de-frag ext drives once a month where you really have to do that with NTFS drives to keep the seek times within reason and to cut down on just general wear and tear on the drive, thus extending the life span of the drive.

---

### Post by Udayakiran on 2010-02-10
> **juancarlospaco said:**
> no.

Why do you say so?

---

### Post by Satoru-san on 2010-02-10
> **juancarlospaco said:**
> no.

NTFS is VERY slow and proprietary. 
Not to mention that it fragments.

NTFS in no way should be used if at all possible.

---

### Post by juancarlospaco on 2010-02-10
NTFS cant handle a path with 256 characters, WTF!!!, think network share file paths, WTF!!!

---

### Post by Kenny_Strawn on 2010-02-10
> **juancarlospaco said:**
> NTFS cant handle a path with 256 characters, WTF!!!, think network share file paths, WTF!!!

In fact, Juan, the only time I would ever use NTFS is when I had to mount a Windows partition. Otherwise, I would always format in Ext4. Even in Jaunty I manually formatted the drive in Ext4 before installing.

---

### Post by juancarlospaco on 2010-02-10
NTFS Locks itself on Hibernation and Power failure, WTF!!!

---

### Post by Udayakiran on 2010-02-10
> **Satoru-san said:**
> NTFS is VERY slow and proprietary. 
Not to mention that it fragments.

NTFS in no way should be used if at all possible.

SLOW: Hard disks ARE slow, so i feel the performance difference is only of academic interest.

PROPRIETARY: Yes, it is. But i dont think the majority of the users would give a rat's rear about that.

FRAGMENTS: Thats a real pain.

> **juancarlospaco said:**
> NTFS cant handle a path with 256 characters, WTF!!!, think network share file paths, WTF!!!

I didnt know that.

---

### Post by lykwydchykyn on 2010-02-10
There is massive misinformation going on in this thread.  I suggest checking here: [http://en.wikipedia.org/wiki/Comparison_of_file_systems](http://en.wikipedia.org/wiki/Comparison_of_file_systems)

Personally, I've had relatively little trouble with either file system.  It's a bit hard to compare since they operate on different operating systems (too many variables).

---

### Post by Udayakiran on 2010-02-10
> **juancarlospaco said:**
> NTFS Locks itself on Hibernation and Power  failure, WTF!!!

What?

---

### Post by Udayakiran on 2010-02-10
> **lykwydchykyn said:**
> There is massive misinformation going on in this thread.  I suggest checking here: [http://en.wikipedia.org/wiki/Comparison_of_file_systems](http://en.wikipedia.org/wiki/Comparison_of_file_systems)

Personally, I've had relatively little trouble with either file system.  It's a bit hard to compare since they operate on different operating systems (too many variables).

Yea, I think Juan has been paid by Linuxsoft to purposefully defame a certain company. :o

BTW, thanks for the link. Both the systems seem pretty equal to me.

---

### Post by lykwydchykyn on 2010-02-10
> **Udayakiran said:**
> What?

You mean what misinformation?

> **juancarlospaco said:**
> NTFS cant handle a path with 256 characters, WTF!!!, think network share file paths, WTF!!!

No, that's not correct.  It has a filename size limit of 255 characters; the total path limit is something like 32k characters.

> **juancarlospaco said:**
> NTFS Locks itself on Hibernation and Power failure, WTF!!!

I don't know what you mean by this.  If you mean what I think you mean, that NTFS volumes can't be mounted under Linux if they're not cleanly shut down, this is a safety feature of the Linux NTFS driver.  

If you mean something else, please explain.

---

### Post by Udayakiran on 2010-02-10
> **lykwydchykyn said:**
> You mean what misinformation?

No. I tried the 'Quick Reply' feature and forgot to check the Quote checkbox. That was a reply to  **juancarlospaco's **post.


> **lykwydchykyn said:**
> 
No, that's not correct.  It has a filename size limit of 255 characters; the total path limit is something like 32k characters.


That i knew. In the case of ext3, the path can be unlimited, but the Filename length is the same as NTFS.

---

### Post by northrup on 2010-02-10
In my experience, they have their advantages and disadvantages.

NTFS is slower due to fragmentation, but I like it's builtin support for compression without having to do some magical Linux voodoo or having to create archives.  It has that built into the filesystem itself, and although it makes things sluggish, I like to have a boot partition (or drive) that's uncompressed, and a second for basic application data that's compressed.  Unfortunately, only Windows seems to support this.

Ext3/4 is a lot faster, so it seems, but my issue with it is that the Windows drivers to support it are on occasion difficult to work with, at least for me.  Sometimes they just fail to read the filesystem for no logical reason.  If it weren't for this, I would be using NTFS only for a Windows boot partition, and all my applications / data on an Ext4 partition once a better driver is out.

Ultimately, it depends on what operating system(s) are installed.  Dual-boot systems (Windows / Linux), in my opinion, would be best with more NTFS, since that can be at least mostly shared between the two.  If a better ext3 driver was made for Windows, I would go the other way and choose an Ext-based filesystem as the one being shared.

I like both.  I wish they, and their respective operating systems, could play nicely.  But that's wishful thinking.

---

### Post by moster on 2010-02-10
NTFS is more advanced then ext3 and 4. That is a fact.

When BTRFS becomes stable, it should be overall "better" then NTFS.

---

### Post by NCLI on 2010-02-10
> **moster said:**
> NTFS is more advanced then ext3 and 4. That is a fact.

When BTRFS becomes stable, it should be overall "better" then NTFS.

What is this "fact" based on? I'm not disputing that it is, I'd just like to know what you base that argument on.

---

### Post by spupy on 2010-02-10
It Works For Me ™.

Ext3, that is. What's up with NTFS links? There are 3 or 4 different types of node links, what do they do? And don't get me started on file permissions...

---

### Post by blur xc on 2010-02-10
> **Kenny_Strawn said:**
> Absolutely not. NTFS does not have a journal, neither is it 64 bit like Ext4.

Note: Ext4 is 64 bit. Ext3 isn't. However, Microsoft does have a 64 bit operating system. What they don't have is a 64 bit FS.

NTFS is a journalling file system- [http://articles.techrepublic.com.com/5100-10878_11-6091177.html](http://articles.techrepublic.com.com/5100-10878_11-6091177.html)

At least to some degree anyway...  I'm not an expert.

BM

---

### Post by mister_pink on 2010-02-10
I'm amazed that noones pointed out the nonsensical logic you've used. 

You said when your linux box crashes it has to do a filesystem check. This is nothing to do with what file system you use, its a safety check that the operating system is doing to make sure there aren't any problems. Its a definite advantage as you don't want to mount a disk if there have been problems until they've been fixed. You say windows doesnt do this on NTFS - so you'd never know if there had been problems then!

---

### Post by falconindy on 2010-02-10
> **Kenny_Strawn said:**
> Absolutely not. NTFS does not have a journal
[http://en.wikipedia.org/wiki/NTFS](http://en.wikipedia.org/wiki/NTFS)
> NTFS has several improvements over FAT and HPFS (High Performance File System) such as improved support for metadata and the use of advanced data structures to improve performance, reliability, and disk space utilization, plus additional extensions such as security access control lists (ACL) and **file system journaling**.

If you want to pick on NTFS, point out its lacking support for:
* Real hard/soft links (Junction points are flakey and Vista's soft links are resolved by the OS, not the FS)
* Reasonable usage of free space (resulting in frequent file fragmentation)
* Simple file permissions (single user systems do NOT need the complexity of ACLs)

On the other hand, NTFS has favorable features over Ext4:
* Transparent compression
* Single instance storage (like KSM, but on a filesystem level)
* Transactional data manipulation (e.g. copy-on-write for volume shadow copies)

Claiming that NTFS is bad because its "not 64 bit" is silly if you understand what 64-bit means for a FS. Hint: it's not the same as 64 bit processing.

---

### Post by kelvin spratt on 2010-02-10
ntfs also does a system check if it crashes but most people press any key to bypass the disk check more fool them.

---

### Post by falconindy on 2010-02-10
> **kelvin spratt said:**
> ntfs also does a system check if it crashes but most people press any key to bypass the disk check more fool them.
e2fsck is a far more advanced tool than chkdsk. You may as well compare a Ford Model T to a top fuel dragster.

---

### Post by Xbehave on 2010-02-10
> When BTRFS becomes stable, it should be overall "better" then NTFS.
"better" BTRFS in it's current state kicks NTFS's ****
[LIST]
[*]Online fsck
[*]better time stamps
[*]better file names
[*]Multi-device support (at many levels)
[*]Real Snapshots (VSS is close, until you actually try and use it)
[*]Data Checksums
[*]Considerably better performance (sure HDDs are slow, but one aim of a FS is to cover that up)
[*]None of the fragmentation causing problems NTFS has
[/LIST]

I can't think of a single way NTFS beats btrfs. Comparing ext to ntfs is unfair because while early reiserfs had problems, it's been miles ahead of ntfs since it became stable (if reiser4 had been mainlined it would probably be up there with ZFS (the reason it wasn't is the same reason ZFS wasn't made for Linux, the changes are too many and too deep for the kernel to accept at once and useless until all are accepted))

---

### Post by Xbehave on 2010-02-10
> **falconindy said:**
> Claiming that NTFS is bad because its "not 64 bit" is silly if you understand what 64-bit means for a FS. Hint: it's not the same as 64 bit processing.
Also last i checked the only ext4 implementation is **just** 48bit, but with changes to make it 64 in mind.

---

### Post by juancarlospaco on 2010-02-10
LOL, dont believe Microsoft documentation, it lies sometimes.

---

### Post by jrusso2 on 2010-02-10
> **Udayakiran said:**
> I know i could be lynched for this, but anyway, is NTFS better than ext3?

I have been using NTFS for about 8-10 years, and never have I lost any data on a NTFS partition. I live in a country where blackouts and brownouts are commonplace. In spite of the frequent power cuts, there has never been data corruption on NTFS. File fragmentation, sure, but no data corruption. 

I've set up a media-server cum torrent-box in a bare bones headless system using Ubuntu server 9.10. And every time after a power failure, I'm having to do a file system check. Thankfully, due to ext3's journalling system, the data is always recovered. But why does it happen? It never happens with NTFS.

So my question is, is NTFS better than ext3?

One of the reasons I won't use any ext file system.  Try a real industrial file system.

---

### Post by fewt on 2010-02-10
> **oldsoundguy said:**
> No .. NTFS allows excessive fragmentation of files in it's management of files.  ext3-4 does NOT.
Not needed to de-frag ext drives once a month where you really have to do that with NTFS drives to keep the seek times within reason and to cut down on just general wear and tear on the drive, thus extending the life span of the drive.

This is not entirely accurate.  With EXT3-4 disk fragmentation occurs as disk space deincreases, or based upon utilization such as the addition / subtraction of very large files over time.

There is a tool for EXT4 called e4defrag which is used as an online defragmentation tool for EXT4 file systems.

Homework before posting guys. ;)

---

### Post by Frak on 2010-02-10
> **Xbehave said:**
> "better" BTRFS in it's current state kicks NTFS's ****
[LIST]
[*]Online fsck
[*]better time stamps
[*]better file names
[*]Multi-device support (at many levels)
[*]Real Snapshots (VSS is close, until you actually try and use it)
[*]Data Checksums
[*]Considerably better performance (sure HDDs are slow, but one aim of a FS is to cover that up)
[*]None of the fragmentation causing problems NTFS has
[/LIST]

I can't think of a single way NTFS beats btrfs. Comparing ext to ntfs is unfair because while early reiserfs had problems, it's been miles ahead of ntfs since it became stable (if reiser4 had been mainlined it would probably be up there with ZFS (the reason it wasn't is the same reason ZFS wasn't made for Linux, the changes are too many and too deep for the kernel to accept at once and useless until all are accepted))

For one, BTRFS is still pretty unstable, so while it does do all that, it also has the ability to make fail sauce in the morning. The reason ZFS isn't on Linux is licensing issues. It's impossible to meet the conditions of both licenses (CDDL and GPL) at once. It can be run in userland, but not kernel mode.

> **juancarlospaco said:**
> LOL, dont believe Microsoft documentation, it lies sometimes.

When wrong, type 'lies'. There was a meme on 4chan about this once.

---

### Post by Xbehave on 2010-02-10
> **fewt said:**
> This is not entirely accurate.  With EXT3-4 disk fragmentation occurs as disk space deincreases, or based upon utilization such as the addition / subtraction of very large files over time.

There is a tool for EXT4 called e4defrag which is used as an online defragmentation tool for EXT4 file systems.

Homework before posting guys. ;)
ext will only fragment when you add a file more than the biggest block of continuous space, it is almost never an issue and there are a few tools to fix it available (e4defrag just does it at a lower level). So while it does get fragmented it's not nearly as bad as NTFS (which in turn is miles better than FAT)

---

### Post by fewt on 2010-02-10
> **Kenny_Strawn said:**
> Absolutely not. NTFS does not have a journal, neither is it 64 bit like Ext4.

Note: Ext4 is 64 bit. Ext3 isn't. However, Microsoft does have a 64 bit operating system. What they don't have is a 64 bit FS.

NTFS (New Technology File System) has been journaled since it's inception.  It also supports encryption, transactional operations (IE Rollback), and symlinks.

I would like to see some supporting documentation that it isn't a 64-bit filesystem because I'm not entirely sure about that.  It's ability to store files that are 16EB in size implies that you are incorrect.

---

### Post by Xbehave on 2010-02-10
> **Frak said:**
> For one, BTRFS is still pretty unstable, so while it does do all that, it also has the ability to make fail sauce in the morning.
Cool story bro, only i've been using btrfs on a highly unstable laptop (both sofware (KMS on latest kernel) and hardware issues) and have seen 0 corruption.

> The reason ZFS isn't on Linux is licensing issues.
ZFS can be reimplemented and shimed into kernel space (See nvidia), but the shims/reimplementation does far too much to the existing VFS layer. 

It's ok to run proprietary modules on a GPL kernel but a CDDL module would be impossible? NO, it's down to technical issue, the legal side is minor.

---

### Post by fewt on 2010-02-10
> **Xbehave said:**
> ext will only fragment when you add a file more than the biggest block of continuous space, it is almost never an issue and there are a few tools to fix it available (e4defrag just does it at a lower level). So while it does get fragmented it's not nearly as bad as NTFS (which in turn is miles better than FAT)

I hope you realize that your largest contiguous free block size decreases as your disk fills.

Which is what I said in my post.

[http://kernelnewbies.org/Ext4#head-38e6ac2b5f58f10989d72386e6f9cc2ef7217fb0](http://kernelnewbies.org/Ext4#head-38e6ac2b5f58f10989d72386e6f9cc2ef7217fb0)

;)

---

### Post by Giant Speck on 2010-02-10
> **Xbehave said:**
> Cool story bro, only i've been using btrfs on a highly unstable laptop (both sofware (KMS on latest kernel) and hardware issues) and have seen 0 corruption.

Ah, the classic "works for me, so your point is invalid" defense.

---

### Post by Kenny_Strawn on 2010-02-10
> **fewt said:**
> NTFS (New Technology File System) has been journaled since it's inception.  It also supports encryption, transactional operations (IE Rollback), and symlinks.

I would like to see some supporting documentation that it isn't a 64-bit filesystem because I'm not entirely sure about that.  It's ability to store files that are 16EB in size implies that you are incorrect.

It may have plenty of features, but with more features comes less performance. This is why NTFS gets as fragmented as it does. Ext4 only gets fragmented under one condition: when files become too large for it to handle. If this happens, just defrag it with an online utility.

---

### Post by fewt on 2010-02-10
> **Kenny_Strawn said:**
> It may have plenty of features, but with more features comes less performance. This is why NTFS gets as fragmented as it does. Ext4 only gets fragmented under one condition: when files become too large for it to handle. If this happens, just defrag it with an online utility.

Please click the link above to read about fragmentation on the kernel newbies site.

Please educate yourself on NTFS and EXT[34] before posting.

---

### Post by Frak on 2010-02-10
> **Xbehave said:**
> It's ok to run proprietary modules on a GPL kernel but a CDDL module would be impossible? NO, it's down to technical issue, the legal side is minor.

Wow, you have no idea how the Nvidia module works. The module is Open Source, but works through a proprietary module in userspace. I know what I'm talking about, you don't.

Just to shove it in your face: [http://kerneltrap.org/node/8066](http://kerneltrap.org/node/8066)

---

### Post by falconindy on 2010-02-10
> **Xbehave said:**
> "better" BTRFS in it's current state kicks NTFS's ****
[LIST]
[*]Online fsck
[*]better time stamps
[*]better file names
[*]Multi-device support (at many levels)
[*]Real Snapshots (VSS is close, until you actually try and use it)
[*]Data Checksums
[*]Considerably better performance (sure HDDs are slow, but one aim of a FS is to cover that up)
[*]None of the fragmentation causing problems NTFS has
[/LIST]

I can't think of a single way NTFS beats btrfs. Comparing ext to ntfs is unfair because while early reiserfs had problems, it's been miles ahead of ntfs since it became stable (if reiser4 had been mainlined it would probably be up there with ZFS (the reason it wasn't is the same reason ZFS wasn't made for Linux, the changes are too many and too deep for the kernel to accept at once and useless until all are accepted))
No such thing as an online fsck. You must mean online defrag. Running btrfsck on a mounted partition will result in hundreds of false positives (errors). Not sure what you're referring to when you say "better" time stamps and file names. The "better" data checksumming is really only a bonus for those with Intel Core processors (which have a hardware level crc32 instruction).

Btrfs's current implementation is actually a little slower than Ext4 for day to day operations, despite all the regressions in the 2.6.32 kernel. I notice this particularly when deleting and unzipping large source trees (e.g. building a kernel or chromium).

It should be noted that Btrfs **does not journal**. While it supports non-ACID conforming transactions, it's only available to privileged processes for security reasons. This does actually have it advantages, but it does make data recovery a little more sketch in the case of even a minor corruption. Also, similar to ReiserFS, if your B-Trees get corrupted, you'd better have a backup. In this regard, NTFS wins in the realm of reliability.

edit: Btrfs itself isn't going to magically eat your cat one day. The stability warning plastered all over the place is about the format. Mason and friends have pledged that the format **will not change** unless they discover an impass that leaves them with no other choice. I've been running about 1.5TB of data across 3 partitions on Btrfs since December and have not had a single issue yet.

---

### Post by Xbehave on 2010-02-10
> **falconindy said:**
> No such thing as an online fsck. You must mean online defrag.
No i mean what i said, online fsck means only very basic integrity checks are needed while booting the rest can be done while the partition is mounted.

> Running btrfsck on a mounted partition will result in hundreds of false positives (errors).
No it doesn't, I just did it.

> Not sure what you're referring to when you say "better" time stamps and file names.
Timestamps are 100x more accurte and have a wider range of valid dates

> The "better" data checksumming is really only a bonus for those with Intel Core processors (which have a hardware level crc32 instruction).
NTFS doesn't have checksumming AFAIK, crc32 can be implemented in software too so file integrity is an option for all users.

> It should be noted that Btrfs **does not journal**.
it's a COW file system so as i understand it it doesn't need a journal (much like nilfs does not)

> Also, similar to ReiserFS, if your B-Trees get corrupted, you'd better have a backup. In this regard, NTFS wins in the realm of reliability.
It should be noted that Btrfs was redesigned to minimise the flaws that cropped up in reiserfs, so is unlikely to be as unstable as early reiserfs was.

> Ah, the classic "works for me, so your point is invalid" defense
Or simply, the "just because you say it's unstable, doesn't mean it's true, why don't you try running it before claiming as such" defence.

> I hope you realize that your largest contiguous free block size decreases as your disk fills.

Which is what I said in my post.
You sure are argumentative for somebody i'm agreeing with, my point was simply that AFAIK NTFS fragments more readily than ext4, without making filesystem operations much more costly, you can't get much better than ext (well you can get reiser, but that prevents a different type of fragmentation).

---

### Post by Satoru-san on 2010-02-10
Back when I was in college, I took a linux class and my teacher said that the max filesize on ext3 was 2gb, I told him that he was full of crap, I have dvd isos that are 4.2 gigs! Then he said something outrageous, something about NTFS supporting like 10 TB files o_O

This is obiously wrong.

Max file size 16 [GiB]("http://en.wikipedia.org/wiki/Gibibyte") – 2 [TiB]("http://en.wikipedia.org/wiki/Tebibyte")

SOURCE: [http://en.wikipedia.org/wiki/Ext3](http://en.wikipedia.org/wiki/Ext3)

---

### Post by falconindy on 2010-02-10
> **Xbehave said:**
> No i mean what i said, online fsck means only very basic integrity checks are needed while booting the rest can be done while the partition is mounted.
Very strange. Looks like the spec for btrfs calls for an online fsck, but based on the last time I ran btrfsck on my mounted root (accidentally) I don't believe that its implemented (yet).

> **Xbehave said:**
> it's a COW file system so as i understand it it doesn't need a journal (much like nilfs does not)
These things aren't really related. Copy on write says that if multiple callers ask for the same resource, they're all given the same handle. Once a caller attempts to modify the resource, a new private copy is created. Changes are made on the private copy until all handles on the original resource are closed -- at which point its discarded from the tree. In order for COW to be effective as a means of data integrity, it would need to keep track of all the old discarded pointers every time a COW occurs. That sounds an awful lot like a journal.

To say that NILFS doesn't journal is mincing words. It's a log structure filesystem AKA journaling to the extreme, where your metadata IS the data.

> **Xbehave said:**
> NTFS doesn't have checksumming AFAIK, crc32 can be implemented in software too so file integrity is an option for all users.
The checksum functionality is necessarily mainly for the RAID capabilities of Btrfs, but it's also done because of the lack of a journal. The software implementation of crc32 is also sloooooow compared to the SSE4.2 instruction.

> **Xbehave said:**
> It should be noted that Btrfs was redesigned to minimise the flaws that cropped up in reiserfs, so is unlikely to be as unstable as early reiserfs was.
Reiser3 still has this weakness. I don't know enough about Reiser4 to say whether or not it still exists (I suspect it doesn't), but we're still a ways away from seeing Reiser4 make it to mainline.

---

### Post by Gallahhad on 2010-02-10
> **Udayakiran said:**
> I know i could be lynched for this, but anyway, is NTFS better than ext3?

I have been using NTFS for about 8-10 years, and never have I lost any data on a NTFS partition. I live in a country where blackouts and brownouts are commonplace. In spite of the frequent power cuts, there has never been data corruption on NTFS. File fragmentation, sure, but no data corruption. 

I've set up a media-server cum torrent-box in a bare bones headless system using Ubuntu server 9.10. And every time after a power failure, I'm having to do a file system check. Thankfully, due to ext3's journalling system, the data is always recovered. But why does it happen? It never happens with NTFS.

So my question is, is NTFS better than ext3?
It's not a question of "better", it's a question of compatibility. 
I have not even looked into which is better, though I have seen some performance testing, that seems to point at ext3 being faster.
But, if I want every OS that is currently used in a real way to have access to a file system, I will use NTFS.
What good is a "better" or a "faster" file system if only 1% can use it reliably?
ext3 for my Linux OS, for everything else NTFS.
Yes, yes, I know, there are ext3 drivers for Windows and Mac, but they suck, and I would not bother other people with them, nor would I want them mounting my ext3 file system with them, they'd hose my stuff up.

What I want to know is, where is WinFS?

---

### Post by Kenny_Strawn on 2010-02-10
> **Gallahhad said:**
>  What I want to know is, where is WinFS?

Dead a long time ago, and really, it was supposed to be something like FUSE, not really a true filesystem. It really was suppoosed to be like a markup service for NTFS, and only hinder performance as a result.

However, maybe WinFS's functionality still exists, in the form of Windows 7's Libraries. Apparently so, because even though Libraries really are like metafiles linking to files across the HDD, they are like WinFS because they allow you to search and categorize your files in a database.

---

### Post by Regenweald on 2010-02-10
> **Kenny_Strawn said:**
> Dead a long time ago, and really, it was supposed to be something like FUSE, not really a true filesystem. It really was suppoosed to be like a markup service for NTFS, and only hinder performance as a result.

However, maybe WinFS's functionality still exists, in the form of Windows 7's Libraries. Apparently so, because even though Libraries really are like metafiles linking to files across the HDD, they are like WinFS because they allow you to search and categorize your files in a database.

Everything you post worries me now ;)

---

### Post by toupeiro on 2010-02-11
Just tonight, I had to recover and manually rebuild a completely destroyed NTFS partition, index, and BCD...  Why?  because suspend didn't suspend properly and it absolutely cratered the OS.  No, NTFS is nowhere near better than ext*  Not by any close account.

---

### Post by Post Monkeh on 2010-02-12
> **lykwydchykyn said:**
> Y

No, that's not correct.  It has a filename size limit of 255 characters; the total path limit is something like 32k characters.




is that definite?

i used to have problems when certain files were copied deep into the folder system (maybe in the 6th or 7th folder) and they ended up inaccessible and un-deletable, yet when they were moved up the folder chain they were fine.  in fairness they did have long filenames themselves (maybe 200 + characters), but i always just assumed it was the total length of the file path, but there's no way it was 32000 characters, the folders weren't any more than 20 characters each, and even going through 6 would only give you 125 characters & the filename.

maybe i was just experiencing a bug

---

### Post by fewt on 2010-02-12
> **Post Monkeh said:**
> is that definite?

i used to have problems when certain files were copied deep into the folder system (maybe in the 6th or 7th folder) and they ended up inaccessible and un-deletable, yet when they were moved up the folder chain they were fine.  in fairness they did have long filenames themselves (maybe 200 + characters), but i always just assumed it was the total length of the file path, but there's no way it was 32000 characters, the folders weren't any more than 20 characters each, and even going through 6 would only give you 125 characters & the filename.

maybe i was just experiencing a bug

Yes, it's well documented.

---

### Post by texaswriter on 2010-02-12
> **northrup said:**
> In my experience, they have their advantages and disadvantages.

NTFS is slower due to fragmentation, but I like it's builtin support for compression without having to do some magical Linux voodoo or having to create archives.  It has that built into the filesystem itself, and although it makes things sluggish, I like to have a boot partition (or drive) that's uncompressed, and a second for basic application data that's compressed.  Unfortunately, only Windows seems to support this.

Ext3/4 is a lot faster, so it seems, but my issue with it is that the Windows drivers to support it are on occasion difficult to work with, at least for me.  Sometimes they just fail to read the filesystem for no logical reason.  If it weren't for this, I would be using NTFS only for a Windows boot partition, and all my applications / data on an Ext4 partition once a better driver is out.

Ultimately, it depends on what operating system(s) are installed.  Dual-boot systems (Windows / Linux), in my opinion, would be best with more NTFS, since that can be at least mostly shared between the two.  If a better ext3 driver was made for Windows, I would go the other way and choose an Ext-based filesystem as the one being shared.

I like both.  I wish they, and their respective operating systems, could play nicely.  But that's wishful thinking.

YOu can actually have partitions individually formatted to different file systems. NTFS on my windows partition and EXT3 on my Ubuntu partition on my laptop.. 

FWIW

---

### Post by lykwydchykyn on 2010-02-12
> **texaswriter said:**
> YOu can actually have partitions individually formatted to different file systems. NTFS on my windows partition and EXT3 on my Ubuntu partition on my laptop.. 

FWIW

I think northrup is referring to having a shared partition for data between the two OS's.

---

### Post by texaswriter on 2010-02-12
> **lykwydchykyn said:**
> I think northrup is referring to having a shared partition for data between the two OS's.

AH, OK, I can't see why somebody would choose to do that, especially considering Linux can see NTFS partitions and mount them [accessing ALL files given root]... 

Both Windows and Linux boot disks have no problem partitioning or resizing. I actually created my partitions with a Windows 7 install disk and then modified and reformatted the linux one from ntfs to ext3... 

It is not a problem to do this, so, occam's razor would suggest: don't do the unnecessary when cutting the unnecessary out accomplishes the same tasks with less effort and less pain. 

K.I.S.S. = **keep it simple and stupid. **

---

### Post by UnixBASHparty on 2010-02-13
NTFS has quite a few features that ext3 is missing. NT permissions are nicer than the POSIX ones.

---

