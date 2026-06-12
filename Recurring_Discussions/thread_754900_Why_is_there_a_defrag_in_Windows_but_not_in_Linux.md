---
title: "Why is there a defrag in Windows but not in Linux"
date: 2008-04-14
forum: Recurring Discussions
---

### Post by Black Mage on 2008-04-14
I'm taking the class Operating Systems in college and we were going over the file systems. He started talking about defragging hard drives in Windows to create space so I asked how come Windows has defrag but Linux and Mac(FreeBSD) doesn't have defrag.

And he stuttered and stammered and admitted to not knowing. SCORE ONE FOR THE STUDENT WITH THE AWESOME QUESTION.

But anyway, how come Windows has defrag and other Operating Systems do not?

---

### Post by paul101 on 2008-04-14
because linux doesnt need defrag because it is a far superiour os :)

---

### Post by TeraDyne on 2008-04-14
There IS a defrg app for EXT2, though I don't know the name of it off the top of my head. In reality, though, it doesn't need it. The EXT\Riser\HFS filesystems don't fragment as easily as FAT\NTFS, IIRC.

---

### Post by Kinst on 2008-04-14
Because of the nature of how unix-based operating systems save things. As I understand it, fragmentation to the extent that you'd see in windows doesn't occur.

---

### Post by bonzodog on 2008-04-14
[http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting](http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting)

This is as best an answer I can get to.

Simply put, FAT and NTFS are inferior filesystems to such things like ReiserFS, Ext3, etc.

---

### Post by insane_alien on 2008-04-14
the more you use the filesystem, the better organised it gets.

use it rarely and the performance degradation probably won't matter/be noticabe anyway.

---

### Post by K.Mandla on 2008-04-14
Not to belittle the question at all, but it's been discussed hundreds of times around here. 

Moved to Recurring Discussions.

---

### Post by LaRoza on 2008-04-14
> **Black Mage said:**
> I'm taking the class Operating Systems in college and we were going over the file systems. He started talking about defragging hard drives in Windows to create space so I asked how come Windows has defrag but Linux and Mac(FreeBSD) doesn't have defrag.

And he stuttered and stammered and admitted to not knowing. SCORE ONE FOR THE STUDENT WITH THE AWESOME QUESTION.

But anyway, how come Windows has defrag and other Operating Systems do not?

Defragging, Restore Points, and antivirus and anti-malware are to counter the weaknesses of Windows, not good features.

---

### Post by DrMega on 2008-04-14
> **LaRoza said:**
> Defragging, Restore Points, and antivirus and anti-malware are to counter the weaknesses of Windows, not good features.

I like the idea of restore points, although the Windows XP implementation of them is very poor. A few times I have temporarily bust my setup by installing and uninstalling the wrong stuff. My fault entirely and usually easy to fix, but it would be great if you could just say "Put it back to how it was yesterday", without having to restore from backup.

---

### Post by hauge on 2008-04-14
Unix does ot need a defragmentation algorithm due to the way that diskspace is allocated. 5% of the filesystem capacity is by default reserved for the user root which gives the operating system a chance for allocating blocks on the disk close to each other.
Another Unix filesystem concept is cylinder groups, where the disk block allocation algorithm tries to keep all datablocks that is part of the same file inside within the same cylindergroup if possible.

These facilities does not exist in windows filesystems.

Regards
Jan

---

### Post by LaRoza on 2008-04-14
> **DrMega said:**
> I like the idea of restore points, although the Windows XP implementation of them is very poor. A few times I have temporarily bust my setup by installing and uninstalling the wrong stuff. My fault entirely and usually easy to fix, but it would be great if you could just say "Put it back to how it was yesterday", without having to restore from backup.

[http://ubuntuforums.org/showthread.php?p=4249544](http://ubuntuforums.org/showthread.php?p=4249544)

I have the new version working and tested. It can restore and backup files easily.

However, at the moment, it has no GUI, and is limited to certain system files, but more can be easily added.

My next step is to make it possible to extend the backup and restore capabilities using user defined rules.

(It is not released yet, but suggestions on that thread are welcome as to features desired)

---

### Post by Tundro Walker on 2008-04-14
Ignore all the other answers.  They don't know what they're talking about.

You see, Linux doesn't need a defragger, because when its running, it creates a localized, dimensional pocket that it buffers disk content through.  When you add new data to your disk, it isn't written directly to disk, instead it gets piped through the quantum dimensional flux, where it's rearranged using Schrodinger's principle of Mass Dynamics, which, based on Chaos Theory, organizes itself through a random cascade paradox and ultimately writes everything in perfect sequence to your disk.  Due to Torvald's advances in Heizenberg's theory of Cross Co-Location, Linux can do all this practically instantaneously, so, once again we're just limited by how fast the hard disk can write the data.

Or was it fairies?  I get Linux and Mac confused sometimes ...

---

### Post by articpenguin on 2008-04-14
> **hauge said:**
> Unix does ot need a defragmentation algorithm due to the way that diskspace is allocated. 5% of the filesystem capacity is by default reserved for the user root which gives the operating system a chance for allocating blocks on the disk close to each other.
Another Unix filesystem concept is cylinder groups, where the disk block allocation algorithm tries to keep all datablocks that is part of the same file inside within the same cylindergroup if possible.

These facilities does not exist in windows filesystems.

Regards
Jan

the cylinder and block groups are a feature of ext2/3/4

---

### Post by articpenguin on 2008-04-14
one advantage of open source is you can read how stuff works unlike windows or some parts of mac os x. 


 * There are two policies for allocating an inode.  If the new inode is
 * a directory, then a forward search is made for a block group with both
 * free space and a low directory-to-inode ratio; if that fails, then of
 * the groups with above-average free space, that group with the fewest
 * directories already is chosen.
 *
 * For other inodes, search forward from the parent directory\'s block
 * group to find a free inode.



* @start:		the starting block (group relative) to find next
 *			allocatable block in bitmap.
 * @bh:			bufferhead contains the block group bitmap
 * @maxblocks:		the ending block (group relative) for the search
 *
 * Find an allocatable block in a bitmap.  We honor both the bitmap and
 * its last-committed copy (if that exists), and perform the "most
 * appropriate allocation" algorithm of looking for a free block near
 * the initial goal; then for a free byte somewhere in the bitmap; then
 * for any free bit in the bitmap.
 */


seems to me ext3 likes keeping the data blocks in the same block group as the inode.

NTFS likes throwing the data on the first contigous free space.

---

### Post by pjkoczan on 2008-04-14
I've seen *nix filesystems fragment. Of course, they were on very busy mail servers and database servers. Honestly, there are some workloads that will cause fragmentation no matter what filesystem is being used. Usually these involve large files with lots of updates on a busy computer.

The difference between Windows and Linux with regard to fragmentation has two main points:

- Linux filesystems do their best to prevent fragmentation (smart allocation of disk blocks, good use of memory buffers, a separate swap partition). Even if a bad workload is encountered and fragmentation happens, it won't fragment as badly.

- Linux filesystems don't fragment under "normal" usage scenarios...the small, mostly-static file scenarios.

---

### Post by Erunno on 2008-04-14
Linux filesystems (i.e. ext2/3) suffer from fragmentation as well, the reason why there was no defrag tools for ext3 is that nobody bothered to write one until now. ext4 will feature an online defragmentation tool. Other highly sophisticated filesystems like XFS had online defragmentation for years. People have been spreading the propaganda that ext3 does not need for years just to cover up a deficiency of their filesystem of choice. For further information about anti-fragmentation strategies in ext4 I recommend the following article:

[https://ols2006.108.redhat.com/2007/Reprints/sato-Reprint.pdf]("https://ols2006.108.redhat.com/2007/Reprints/sato-Reprint.pdf")

Oh, and claiming that NTFS is inferior pretty much exposes some heavy bias against Microsoft. Considering that NTFS was designed in the early 90s and released in 1993 it was one, if not the most modern filesystem around. Unicode character encoding, metadata support, transparent encryption and compression, 64-bit addressing, etc... NTFS had it all, over 15 years ago. I recommend the following Ars Technica article to learn how ridiciously far ahead of its competition NTFS was when it was released (and still is in some aspects):

[http://arstechnica.com/articles/paedia/past-present-future-file-systems.ars/6]("http://arstechnica.com/articles/paedia/past-present-future-file-systems.ars/6")

---

### Post by LaRoza on 2008-04-14
> **Erunno said:**
> 
Oh, and claiming that NTFS is inferior pretty much exposes some heavy bias against Microsoft. Considering that NTFS was designed in the early 90s and released in 1993 it was one, if not the most modern filesystem around. Unicode character encoding, metadata support, transparent encryption and compression, 64-bit addressing, etc... NTFS had it all, over 15 years ago. I recommend the following Ars Technica article to learn how ridiciously far ahead of its competition NTFS was when it was released (and still is in some aspects):

[http://arstechnica.com/articles/paedia/past-present-future-file-systems.ars/6]("http://arstechnica.com/articles/paedia/past-present-future-file-systems.ars/6")

NTFS may be good, but it may not be. Where are the specs for it?

---

### Post by Erunno on 2008-04-14
> **LaRoza said:**
> NTFS may be good, but it may not be. Where are the specs for it?

Not sure what you intend with this remark. Do you claim that these features never existed?

Anyway, since NTFS specifications have never been disclosed by Microsoft the closest you'll get are the ones reverse-engineered by the NTFS-3G developers:

[http://www.ntfs-3g.org/index.html]("http://www.ntfs-3g.org/index.html")

---

### Post by SunnyRabbiera on 2008-04-14
Really there is no defrag needed in most unix/ unix like filesystems as they can handle themselves better then windows filesystems.
Now dont get me wrong, NTFS is actually pretty solid for a MS made file system, but something that fragments that much is more trouble then what it is worth.

---

### Post by Erunno on 2008-04-14
> **SunnyRabbiera said:**
> Really there is no defrag needed in most unix/ unix like filesystems as they can handle themselves better then windows filesystems.
Now dont get me wrong, NTFS is actually pretty solid for a MS made file system, but something that fragments that much is more trouble then what it is worth.

So, why did the ext4 developers suddenly see the need for all kinds of anti-fragmentation measures (some lifted straight from XFS) including online defragmentation? Can't be because ext3 was causing fragmentation over time as this would topple some pipe dreams about non-fragmenting Linux filesyystems...

---

### Post by akiratheoni on 2008-04-14
I don't think a lot of the people here mean that it's impossible to fragment an ext3 file system. Of course you will have to defrag eventually but definitely not as nearly as often as Windows. 

Personally I have had no need to defrag my ext3 system and I'm sure others haven't had to. It doesn't mean ext3 is impossible to fragment though, it just means fragmenting is rare.

---

### Post by SunnyRabbiera on 2008-04-14
> **Erunno said:**
> So, why did the ext4 developers suddenly see the need for all kinds of anti-fragmentation measures (some lifted straight from XFS) including online defragmentation? Can't be because ext3 was causing fragmentation over time as this would topple some pipe dreams about non-fragmenting Linux filesyystems...
well they might have done it as a just in case measure, hey at least they are thinking ahead...

---

### Post by articpenguin on 2008-04-14
from wikipedia


Defragmentation

There is no online ext3 defragmentation tool working on the filesystem level. An offline ext2 defragmenter, e2defrag, exists but requires that the ext3 filesystem be converted back to ext2 first. But depending on the feature bits turned on the filesystem, e2defrag may destroy data; it does not know how to treat many of the newer ext3 features.[7]

There are userspace defragmentation tools like Shake[8] and defrag [9]. Shake works by allocating space for the whole file bolt upright and hoping that it will make the newly allocated file less fragmented. It also tries to write files used at the same time next to each others. Defrag works by copying each file over itself.
However they only work if the filesystem is reasonably empty. A true defragmentation tool does not exist for ext3.[10]

That being said, as the Linux System Administrator Guide states, "Modern Linux filesystem(s) keep fragmentation at a minimum by keeping all blocks in a file close together, even if they can't be stored in consecutive sectors. Some filesystems, like ext3, effectively allocate the free block that is nearest to other blocks in a file. Therefore it is not necessary to worry about fragmentation in a Linux system."[11]

Irrespective of the above (subjective) statement, file fragmentation can be an important issue in server environments such as in multi-media server applications. While it is true that ext3 is more resistant to file fragmentation than FAT filesystems, nonetheless ext3 filesystems can and do get fragmented over time. Consequently the successor to the ext3 filesystem, ext4, includes a filesystem defragmentation utility and support for extents (contiguous file regions).

Further examples in which lack of defragmentation in some Linux filesystems (such as ext3) is a serious issue, includes server applications where rapid, concurrent and random file creation, update or access occurs. Such systems include large-scale carrier grade voice mail systems, Media-Messaging Service Centers (MMSCs) and SMS/SMSCs (Short Message Service Centers) servers. Media servers such as large scale voice mail and UMS servers are required to stream hundreds of voice or video streams concurrently to hundreds of users in near real-time conditions. These types of applications are particularly susceptible to file fragmentation; access delays during playback of a voice (e.g. voice mail) or video file, due to multiple fragmentation in the media file, can lead to playback interruption or distortion. As fragmentation increases over time, service capacity of these systems degrades because of increased CPU and I/O overhead resulting from fragmentation induced disk thrashing.

---

### Post by digger95 on 2008-04-14
> **DrMega said:**
> I like the idea of restore points... a few times I have temporarily bust my setup by installing and uninstalling the wrong stuff. My fault entirely and usually easy to fix, but it would be great if you could just say "Put it back to how it was yesterday", without having to restore from backup.
I agree with this.  I hated system restore in Windows Me, but in XP I got to like it a lot.  Anytime I installed new software I would set a restore point, and it did save my butt a few times when things didn't go so well.  I miss that feature actually.

---

### Post by LaRoza on 2008-04-15
> **digger95 said:**
> I agree with this.  I hated system restore in Windows Me, but in XP I got to like it a lot.  Anytime I installed new software I would set a restore point, and it did save my butt a few times when things didn't go so well.  I miss that feature actually.

Perhaps you could post in that thread I linked to earlier with suggestions.

> **articpenguin said:**
> 

Further examples in which lack of defragmentation in some Linux filesystems (such as ext3) is a serious issue, includes server applications where rapid, concurrent and random file creation, update or access occurs. Such systems include large-scale carrier grade voice mail systems, Media-Messaging Service Centers (MMSCs) and SMS/SMSCs (Short Message Service Centers) servers. Media servers such as large scale voice mail and UMS servers are required to stream hundreds of voice or video streams concurrently to hundreds of users in near real-time conditions. These types of applications are particularly susceptible to file fragmentation; access delays during playback of a voice (e.g. voice mail) or video file, due to multiple fragmentation in the media file, can lead to playback interruption or distortion. As fragmentation increases over time, service capacity of these systems degrades because of increased CPU and I/O overhead resulting from fragmentation induced disk thrashing.

Such systems would not use ext3.

---

### Post by klange on 2008-04-15
Ug, 3 pages and this topic is still going...

There is no defragmenter for ext3 because for any normal use there is no need to defragment. Ext3 is so resilient to fragmentation that unless you use it for the wrong things you'll be fine. However, since people wanted to use it for those wrong things, defragging become a problem - because, no you can't defrag ext3 at all (well, there's no "real" way to do it, but you can convert the file system to ext2 and use an ext2 defragger and then convert back) - Ext4 was designed to remedy this and other problems.

It's really not that complicated.

---

### Post by Erunno on 2008-04-15
> **akiratheoni said:**
> I don't think a lot of the people here mean that it's impossible to fragment an ext3 file system. Of course you will have to defrag eventually but definitely not as nearly as often as Windows. 

Personally I have had no need to defrag my ext3 system and I'm sure others haven't had to. It doesn't mean ext3 is impossible to fragment though, it just means fragmenting is rare.

Is there any scientific (or at least empirical) evidence that NTFS fragments more than ext3? Under what load? What kind of fragmentation?

I'm pretty sure I can find hundreds of thousands of Windows users who'll vouch that never defragmenting their harddrive had any perceivable effect on performence. In my opinion, one of the major reasons why people think NTFS needs defragmentation all the time is the availibility of an easily accesible visualization tool (defrag) which shows some dangerous looking red bars which in turn urges people to defragment all the time (just in case, although I strongly doubt that anybody will notice a difference in I/O performance). 

Since there's no such tool for ext3 (or at least not generally available) people simply have no kind of visualization of the state of fragmentation and therefore simply don't really care.

ext3 suffers from fragmentation ike any other filesystem around, especially when running a for a long time. That's nothing bad per se as it is technically understandable. It is botherseome though that some of the more ardent Linux users try to spin a shortcoming into a feature despite even the developers acknowledging the problem.

---

### Post by Erunno on 2008-04-15
> **SunnyRabbiera said:**
> well they might have done it as a just in case measure, hey at least they are thinking ahead...

Yeah, thinking ahead by (finally) implementing features which other filesystems had for years (and for good reason). Must be it.

---

### Post by Erunno on 2008-04-15
> **LaRoza said:**
> Such systems would not use ext3.

Says who? I can't find any documents from ext3 developers which suggest or discourage specific deployment scenarios. The latest changes merged into ext show that these kind of scenarios are indeed within the planned scope for this filesystem and therefore some necessary corrections had to be made to deal with its shortcomings.

> **WindowsSucks said:**
> There is no defragmenter for ext3 because for any normal use there is no need to defragment. Ext3 is so resilient to fragmentation that unless you use it for the wrong things you'll be fine. However, since people wanted to use it for those wrong things, defragging become a problem - because, no you can't defrag ext3 at all (well, there's no "real" way to do it, but you can convert the file system to ext2 and use an ext2 defragger and then convert back) - Ext4 was designed to remedy this and other problems.

It's really not that complicated.

What is "normal" usage. Can you give me any kind of I/O pattern that one should consider "normal"? And what are the wrong things? Any canonical sources?

---

### Post by LaRoza on 2008-04-15
> **Erunno said:**
> Is there any scientific (or at least empirical) evidence that NTFS fragments more than ext3? Under what load? What kind of fragmentation?

ext3 suffers from fragmentation ike any other filesystem around, especially when running a for a long time. That's nothing bad per se as it is technically understandable. It is botherseome though that some of the more ardent Linux users try to spin a shortcoming into a feature despite even the developers acknowledging the problem.

No, there is no documentation on NTFS, so the only things we know about it are what have been reverse engineered.

> **Erunno said:**
> Says who? I can't find any documents from ext3 developers which suggest or discourage specific deployment scenarios. The latest changes merged into ext show that these kind of scenarios are indeed within the planned scope for this filesystem and therefore some necessary corrections had to be made to deal with its shortcomings.


Says me. I wouldn't use ext3 for a busy server. If you want more information, research the available file systems and their uses.

What is your point? That NTFS isn't bad? You know what, I agree. NTFS is pretty good from what I have seen. However, it is a Windows only file system, and there is no way to use it on Linux. This is a Linux forum you know. 

ext3 is a good file system for the desktop. Is it better than NTFS? I don't know, I don't use NTFS and can't because it isn't available for my operating system.

---

### Post by Erunno on 2008-04-16
> **LaRoza said:**
> No, there is no documentation on NTFS, so the only things we know about it are what have been reverse engineered.

The on-disk structure has been pretty thoroughly reverse-engineered otherwise you'd have data corruption all the time when writing through NTFS-3G. Plus, this does not really answer the original question: Under what load and from what kind of fragmentation does NTFS suffer and how does it compare to other filesystems under the same circumstances?

> Says me. I wouldn't use ext3 for a busy server. If you want more information, research the available file systems and their uses.

There is a difference between
[LIST]
[*]Not intended for a certain use case by design and
[*]Discouraged due to technical limitations.
[/LIST]

The whole point of ext4 was to redeem some of ext shortcomings because it was and is very well intended for some of the use cases for which ext3 has been deemed to be a poor candidate.

> What is your point? 

I'm trying to counter some of the bias which is present on Linux message boards (and probably on the respective Windows and Mac OS X boards as well). Spreading unfounded claims does not really help in creating an informed Linux community. Linux has a lot of advantages compared to its competitors but that's neither a good reason to deny the problem it has nor to downplay this problems by pointing at the (perceived or real) problems other OS have.

> However, it is a Windows only file system, and there is no way to use it on Linux. 

Technically its possible to use NTFS on Linux via NTFS-3G (at least on non-root partitions as far as I know). Ubuntu's next release will be installable on NTFS via Wubi. It's not the preferred solution since the development of NTFS is solely dependent on Microsoft and there may be also legal problems.

> 
This is a Linux forum you know. 

So?

> ext3 is a good file system for the desktop. Is it better than NTFS? I don't know, I don't use NTFS and can't because it isn't available for my operating system.

This was a discussion about advantages and disadvantages of indivdual filesystems on Linux and Windows. Whether a filesystem is available for the OS of your choice is pretty much beside the point.

---

### Post by LaRoza on 2008-04-16
> **Erunno said:**
> The on-disk structure has been pretty thoroughly reverse-engineered otherwise you'd have data corruption all the time when writing through NTFS-3G. Plus, this does not really answer the original question: Under what load and from what kind of fragmentation does NTFS suffer and how does it compare to other filesystems under the same circumstances?

I'm trying to counter some of the bias which is present on Linux message boards (and probably on the respective Windows and Mac OS X boards as well). Spreading unfounded claims does not really help in creating an informed Linux community. Linux has a lot of advantages compared to its competitors but that's neither a good reason to deny the problem it has nor to downplay this problems by pointing at the (perceived or real) problems other OS have.


That is hardly a valid specification. There is no standard to follow. NTFS is not a valid option. Note, NTFS in XP and NTFS in Vista is different, but you would never guess it. It is NTFS. It is the FS behind the curtain. It is hidden to the end user.

If you want to support NTFS, it is up to you to bring up the data. 

Why try to counter the bias? I don't go on Mac OS X forum and try to counter their bias. I don't go on Windows forums and counter their bias. 

If someone has a Windows problem, I don't say "Use EXT3, it is a better file system", as that is not the Windows solution. Although EXT3 is free, and there are ext2 drivers for Windows, Windows could easily have native support.

Windows doesn't allow the use of free existing file systems, Linux does allow the use of non free, hidden file systems AND has provided a way to use some of the free ones on Windows.

Windows comes with a disk defragmenter. Is it needed on NTFS? Who knows. Linux doesn't normally come with such a tool, because it is not needed in a way that justifies its inclusion.

---

### Post by klange on 2008-04-17
> **Erunno said:**
> What is "normal" usage. Can you give me any kind of I/O pattern that one should consider "normal"? And what are the wrong things? Any canonical sources?

Do you use your computer to do regular day-to-day activities or do you run a media upload server? Because the latter is something that shouldn't be done with EXT3 - from what I've heard - and will eventually lead to noticeable fragmentation. I'm not an expert on file systems.

---

### Post by articpenguin on 2008-04-17
from experience the only filesystem in linux that will need defragging is JFS. I had a jfs partition for 6 months and write speeds went down to 5MB/s. I dont have enough experience with reiserfs or xfs as they both corrupt WAY TOO EASY. Ext3 after 9 months slowed down only a little but it was really not noticable.

---

### Post by neyuru on 2008-04-19
> **Erunno said:**
> 
I'm trying to counter some of the bias which is present on Linux message boards (and probably on the respective Windows and Mac OS X boards as well). Spreading unfounded claims does not really help in creating an informed Linux community. Linux has a lot of advantages compared to its competitors but that's neither a good reason to deny the problem it has nor to downplay this problems by pointing at the (perceived or real) problems other OS have.  

Could not agree more with you, I plead to a well informed Linux community with hardstone FACTS, not aggressive users' poorly unfounded comments.

For aggressive windows-biased Linux users out there: ¿Do you think the non-xperienced Linux users are so stupid enough to beleive such claims on the superiority of Linux filesystems against Microsoft's beacuse IT JUST IS? If you want to make a point PROVE IT.

---

### Post by LaRoza on 2008-04-19
> **neyuru said:**
> Could not agree more with you, I plead to a well informed Linux community with hardstone FACTS, not aggressive users' poorly unfounded comments.

For aggressive windows-biased Linux users out there: ¿Do you think the non-xperienced Linux users are so stupid enough to beleive such claims on the superiority of Linux filesystems against Microsoft's beacuse IT JUST IS? If you want to make a point PROVE IT.

There are no facts concerning NTFS. It is a closed standard. To test this, make an "NTFS" file system with a Linux based tool. It works fine in Linux with the appropriate drivers, but doesn't work in Windows!

The Windows NTFS works in Linux because it has been reverse engineered. NTFS changes as Windows gets new versions (XP to Vista in particular). 

Maybe NTFS doesn't fragment that much. Maybe it is as good as EXT3, but we will never know now, will we.

---

### Post by DahVid on 2008-04-19
Some file systems include defragmentation tools and for those that don't you can just move all of the files and move them back (See [Shake](http://vleu.net/shake/))

---

### Post by articpenguin on 2008-04-21
> **DahVid said:**
> Some file systems include defragmentation tools and for those that don't you can just move all of the files and move them back (See [Shake](http://vleu.net/shake/))

shake and other defraggers will only work if there is a lot of contiguous free space. If the free space is very fragmented chances are the file will be more fragmented.

---

