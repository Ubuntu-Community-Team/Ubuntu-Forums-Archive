---
title: "Defragmenting linux hard drives"
date: 2008-11-25
forum: New to Ubuntu
---

### Post by satipera on 2008-11-25
I am assuming there is no sense in this article. [http://www.americanchronicle.com/articles/82757](http://www.americanchronicle.com/articles/82757)

is there?

---

### Post by oldos2er on 2008-11-25
Looks like they're trying hard to sell software.

---

### Post by Olivier2371 on 2008-11-25
Normally Ubuntu doesn't need to be defrag.

---

### Post by mkvnmtr on 2008-11-25
Ha. He is probably right but I "get" to reinstall my Ubuntu often enough that it is not a problem. If I ever get real good at this maybe I will think about the defragmention software that is already around for free.

---

### Post by Crafty Kisses on 2008-11-25
You don't really have to defrag in Linux, the file system is organized and stored more efficiently than a Windows box. If you really want to then I can
suggest you go to something like Google and search "Linux defrag" or something and grab a utility, they do exist, but unnecessary.

There is an option to "clean" though, just run this command in Terminal:
```
sudo apt-get clean
```

---

### Post by Therion on 2008-11-25
Eesh...

The author is obviously a shill for "Stellar Information Systems".  

> Though the noticeable effects could be late (almost when 95% of hard disk becomes full), but the fragmentation in the Linux file systems is the truth.
If your hard drive is 95% full you've got WAAAY bigger problems to be concerned about than any degree of fragmentation.

[Rebuttal arguement](http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting) or, why you don't need to defrag when using EXT2/3.

---

### Post by oldos2er on 2008-11-25
If you use ext3, the only time fragmentation becomes an issue is when the partition is 95% or greater full. I'm certainly far from expert on this subject, but it appears [http://www.americanchronicle.com/articles/82757](http://www.americanchronicle.com/articles/82757) is written to lure Windows users who are ignorant of ext3 into buying their software. ext3 fragmentation is in no way comparable to NTFS fragmentation, since these filesystems differ greatly in the way they write data to a disk.

---

### Post by satipera on 2008-11-25
What does the "clean" option do?

---

### Post by VoodooLoveDog on 2008-11-25
> **satipera said:**
> I am assuming there is no sense in this article. [http://www.americanchronicle.com/articles/82757](http://www.americanchronicle.com/articles/82757)

is there?

Was the article translated from a foreign language? It was very difficult to read.

---

### Post by starcannon on 2008-11-25
[quote=from the page]In ext3 file system, the application demands that it should be converted into Ext2 first. But, this may create a data loss scenario as it may not know how to deal with the new features of Ext3 file system.[/quote]

Heh? Is this just rewriting the partition table or something? I don't quite follow what this software is doing. Anyone know why it needs to convert to ext2 before "defragging"? Another question is, does this matter on a drive that is not >= 95% capacity? For instance, what if the drive is only at 85% capacity, will defragging be of any use? I have used Linux for many years now, and have always read that defragmenting is not something we worry about on the ext2/3 file system. Anyway, I never have defragged my linux partitions, but all the same would like to understand better what the author of the article means, so if any file system afficianado's can fill in some blanks I'd be interested in growing my understanding of things.

Thanks,
starcannon aka Rob

---

### Post by scorp123 on 2008-11-25
> **starcannon said:**
> I don't quite follow what this software is doing. That software is BS. Just forget about it.

> **starcannon said:**
>  Anyone know why it needs to convert to ext2 before "defragging"? Ext3 is journalled. And this BS program seems to do funky stuff to the filesystem, so that any unclean operation might leave unclean metadata behind e.g. the actual contents of the filesystem and the journal all of a sudden do no longer agree about what operation has succeeded and what hasn't succeeded ... Usually Linux would complain here and do a filesystem check upon next reboot. But as this BS-program keeps messing with the filesystem and has no intention of stopping its operations, any error on the filesystem thus has good chances of growing dramatically which in the end might leave you stranded with a totally crippled filesystem.

It seems the authors know about this "little problem" their BS-program might do to a journaled Ext3 system ... hence their insistence that a filesystem be converted back to Ext2 ... no journal = no metadata to worry about. And you won't see what a P.O.S. that BS program really is ;)  Hence their suggestion :D

> **starcannon said:**
>  Another question is, does this matter on a drive that is not >= 95% capacity? For instance, what if the drive is only at 85% capacity, will defragging be of any use? Any filesystem that's beyond 50% capacity is bound to fragment at some point in time. This is normal. But no: you still don't need to defragment. Linux filesystems (Ext3, JFS, XFS, ReiserFS ...) do a way better job at keeping track where all the fragments are located and they really try hard to place fragments of the same file adjacent to each other as much as it is possible. So even if a filesystem gets some heavy use and gets filled up, you still don't have to bother too much about defragmenting. With XFS there is a defrag tool (/usr/sbin/xfs_fsr ... from the "xfsdump" package) but in all these years I have never had to use it. Usually it's enough if you empty a filesystem e.g. by copying large files away (or why not even outright delete what you don't need) and then copying them back one by one ... this should more or less instantly resolve any fragmentation issues. 

> **starcannon said:**
>  I have used Linux for many years now, and have always read that defragmenting is not something we worry about on the ext2/3 file system.  Exactly. "Filesystem fragmentation = big problem = I need to defrag" is Windows-thinking. Just like "I have no firewall = I am not protected". That's all BS created by Microsoft to cover up the shortcomings in their OS products.

As Linux user you can just sit back and relax. Filesystem fragmentation is indeed not something our kind has to worry about.


> **starcannon said:**
>  Anyway, I never have defragged my linux partitions  Years ago I once tried the "xfs_fsr" utility on a well filled 200 GB disk ... it reduced fragmentation by 0.5% ... So instead of 2.5% fragmentation I now had 2% fragmentation. Big deal, LOL. 0.5% of 200 GB happen to be around ~1 GB of data ... that's like 2 CD *.iso images not being exactly in one piece. Oh dear. Big major disaster, LOL.

I never bothered to use that utility again :D

Just forget about defragmentation. Unless you do some really funky stuff you will never ever even realise that anything on your disks got fragemented. It's a fact. ;)

---

### Post by damis648 on 2008-11-25
> **codename said:**
> you don't really have to defrag in linux, the file system is organized and stored more efficiently than a windows box. If you really want to then i can
suggest you go to something like google and search "linux defrag" or something and grab a utility, they do exist, but unnecessary.

There is an option to "clean" though, just run this command in terminal:
```
sudo apt-get clean
```

+1

---

### Post by bodhi.zazen on 2008-11-25
> **oldos2er said:**
> If you use ext3, the only time fragmentation becomes an issue is when the partition is 95% or greater full. I'm certainly far from expert on this subject, but it appears [http://www.americanchronicle.com/articles/82757](http://www.americanchronicle.com/articles/82757) is written to lure Windows users who are ignorant of ext3 into buying their software. ext3 fragmentation is in no way comparable to NTFS fragmentation, since these filesystems differ greatly in the way they write data to a disk.

+1

The "Truth" is every file system will always have some fragmentation, the question is does it affect performance.

In Windows, FAT and NTFS become fragmented enough to affect performance with just daily usage.

This is simply not the case with "standard" usage in Linux. Sure if you fill a disk to 99% capacity and start writing / deleting files you will get fragmentation , but the "problem" here is that the HD is full.

You can check your fragmentation, from a live cd with fsck

```
sudo fsck /dev/sdxy
```

DO NOT RUN THAT ON A MOUNTED FILE SYSTEM, thus from a live CD. sdxy = the partition to check.

---

### Post by fatphilthethird on 2008-11-26
Now this may be all coincidence, but the article is written by one Allen Sood.

A little googleing reveals this link;

[http://www.buzzle.com/authors.asp?author=19699](http://www.buzzle.com/authors.asp?author=19699)

Where someone called Allan Sood describes himself thusly

> i am a student of Mass Communication doing research on data recovery software. I am also a freelancer for [http://www.stellarinfo.com](http://www.stellarinfo.com) and [http://www.photo-recovery-software.com/](http://www.photo-recovery-software.com/)

Stellar Info produces the Stellar Phoenix  Linux Data Recovery software

Make of that what you will

Fat

---

### Post by JNelson on 2008-11-27
In my Experience NTFS allocation policy has been improved in vista.

Ext3 can get quite fragmented even with 80% free space. Ext3 is broken up into block groups. When allocating a new file its policy is that it will stay in the block group. Now if That block groups free space is heavily fragmented than chances are the files in the directory can be fragmented.

---

### Post by Paqman on 2008-11-27
> **Therion said:**
> 
The author is obviously a shill for "Stellar Information Systems".  


Indeed, in fact The "American Chronicle" seems to be some kind of affiliate scheme, so the reliability of the articles in general is highly suspect.

As for ext2/3 fragmentation, it does happen (a little) which is why ext4 will include a defragmenter. Most people will probably never need to use it though, it's intended for certain server setups.

---

### Post by psusi on 2008-11-27
Wow that article is very poor.  It seems to be selling data recovery software, not a defragmenter.  It seems to be saying that if you use the old e2defrag program to defragment, you had to disable the journal ( what they mean by convert to ext2 ) in order to use it, and this could somehow mangically lead to a corrupted filesystem, which you would then need their software to try and recover your data.

The defrag package was removed from Debian about a year ago because it had not been maintained in many years and was abandoned and suffering from bit rot.  This in turn triggered it being removed from Ubuntu.  About two years ago I had patched it in Ubuntu to fix a few bugs it had dealing with ext3.  Right now I'm fixing a few more bugs with dealing with extended attributes/access control lists, and inode sizes larger than 128 bytes, which is now the default in Intrepid.  Once I take care of that, hopefully I can get it back into the repositories in time for Jaunty.

At that point if you are really pedantic or curious, you can try running it and see if you notice any difference, but I'll bet you won't.

---

### Post by satipera on 2008-11-28
I have read a couple of articles about "butter fs" a new filing system that is supposed to be beta released in the new year. Will this make any difference to the average user and to what seems from the previous posts a very minor fragmentation issue?

---

### Post by collinp on 2008-11-28
> **satipera said:**
> I have read a couple of articles about "butter fs" a new filing system that is supposed to be beta released in the new year. Will this make any difference to the average user and to what seems from the previous posts a very minor fragmentation issue?

Never heard of Buffer FS, and I cant seem to find anything in google about it. Anyways, unless you are ripping dvds to your hard drive and it gets extremely full, there is no need for defragmentation for linux in the first place, seeing that ext3 manages files better than anything else that I know of.

---

### Post by jolx on 2008-11-28
> **satipera said:**
> What does the "clean" option do?

it clears the cache of packages downloaded with apt-get

---

### Post by rasmus91 on 2008-11-28
> Rebuttal arguement or, why you don't need to defrag when using EXT2/3.

This was geniuos!

---

### Post by satipera on 2008-11-28
> **Hellow said:**
> Never heard of Buffer FS, and I cant seem to find anything in google about it. Anyways, unless you are ripping dvds to your hard drive and it gets extremely full, there is no need for defragmentation for linux in the first place, seeing that ext3 manages files better than anything else that I know of.

Beg your pardon I meant better fs  not butter fs but you said buffer fs :-) see this article

[http://www.internetnews.com/dev-news/article.php/3781676/A+Better+File+System+for+Linux.htm](http://www.internetnews.com/dev-news/article.php/3781676/A+Better+File+System+for+Linux.htm)

 Will it make any difference to the average user and in particular the new ssd drives?

---

### Post by susanne260 on 2008-11-28
> **bodhi.zazen said:**
> 
You can check your fragmentation, from a live cd with fsck

```
sudo fsck /dev/sdxy
```

DO NOT RUN THAT ON A MOUNTED FILE SYSTEM, thus from a live CD. sdxy = the partition to check.


I just ran a check on my Ubuntu Hardy installation (which I have used for about 2 months), and here's the output:

```
ubuntu@ubuntu:~$ sudo fsck /dev/sdb1
fsck 1.41.3 (12-Oct-2008)
e2fsck 1.41.3 (12-Oct-2008)
/dev/sdb1 has been mounted 25 times without being checked, check forced.
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
/dev/sdb1: 130702/30146560 files (2.7% non-contiguous), 10893679/120577857 blocks
```

Does that mean it's 2.7% fragmented?

If yes, then that's kind of strange, because the size of that partition is about 460GB and about 91% of it is free space. Moreover it has never had less than 90% of free space. Screenshot: [http://i37.tinypic.com/69jhfp.png](http://i37.tinypic.com/69jhfp.png)

Or does the 2.7% mean something else? :D

---

### Post by hyper_ch on 2008-11-28
I like to add this here:

[http://tldp.org/HOWTO/Partition/appendix.html](http://tldp.org/HOWTO/Partition/appendix.html)

> None of these habits should be carried over to Linux and ext2. Linux native file systems do not need defragmentation under normal use and this includes any condition with at least 5% of free space on a disk. There is a defragmentation tool for ext2 called defrag, but users are cautioned against casual use. A power outage during such an operation can trash your file system. Since you need to back up your data anyway, simply writing back from your copy will do the job. 

---

### Post by bodhi.zazen on 2008-11-28
> **susanne260 said:**
> < clip> 
/dev/sdb1: 130702/30146560 files (2.7% non-contiguous), 10893679/120577857 blocks[/code]Does that mean it's 2.7% fragmented?

If yes, then that's kind of strange, because the size of that partition is about 460GB and about 91% of it is free space. Moreover it has never had less than 90% of free space. Screenshot: [http://i37.tinypic.com/69jhfp.png](http://i37.tinypic.com/69jhfp.png)

Or does the 2.7% mean something else? :D

That means that your file system is 2.7 % fragmented. 

I am not sure how the % is calculated , but would assume it has to do with the % of files and not % of total disk capacity.

I think you should ask yourself what do these numbers mean and why do they bother you ?

Take a look at Windows :

[http://blogs.technet.com/askperf/archive/2008/03/14/disk-fragmentation-and-system-performance.aspx](http://blogs.technet.com/askperf/archive/2008/03/14/disk-fragmentation-and-system-performance.aspx)

Notice the output of the analysis :

[IMG]http://blogs.technet.com/blogfiles/askperf/WindowsLiveWriter/DiskFragmentationandSystemPerformance_7C89/image_3.png[/IMG]

7% fragmentation for windows, and they do not advise defragmentating the file system.

See also this "white paper"

[http://www.onwindows.com/Articles/White-paper-The-impact-of-disk-defragmentation/2364/Default.aspx](http://www.onwindows.com/Articles/White-paper-The-impact-of-disk-defragmentation/2364/Default.aspx)

Notice the fragmentation on the test system > ranged from 5% to 1489%**1489 %** :shock:

:lolflag:

As I said, every file system will have *some* fragmentation. The question is how much is acceptable and at what point does it affect performance ?

In regards to ext4, yes it will have a defragmentation tool, but that is not all.

[http://en.wikipedia.org/wiki/Ext4](http://en.wikipedia.org/wiki/Ext4)

---

### Post by psusi on 2008-11-28
fsck just divides the number of files that are not 100% contiguous by the number of total files on the disk.  I recently noticed it has a bit of a bug though that causes it to report any file over 44kb as not contiguous because once the file grows past 11 blocks, the 12th block is used as the indirect block to store the addresses of the remaining blocks of the file.  It seems that fsck looks at a file with 13 blocks and sees that the 12th block on the disk is the indirect block, not file data, and since it separates blocks 1-11 from blocks 12 and 13, it says the file is fragmented.

At the end of the day, they only time you will be affected by fragmentation is if a small file, like your 25 meg mail box, is broken into many fragments, like 100.  This is what tends to happen on Windows and why it needs defragged all the time.  A large file, like an iso image, being split into 4 fragments isn't going to be noticed, but fsck will tell you that it isn't contiguous.

---

### Post by CatKiller on 2008-11-28
As hyper_ch quoted, if you're backing up your data anyway before you do the operation, restoring from your backup is all the defrag tool you need.

---

### Post by drlmg on 2008-12-02
Great !!! You guys have inadvertently solved a problem that I have been plagued with for almost 2 years. I have several NAS drives all of which are formatted in one or another of the linux formats. I move large files on and off them regularly. Having used NTFS / windows for years and being new to linux I thought I had to defrag the drives. The drives have ethernet and USB connections but not the USB connection that allows me to hook up directly to my PC. This posed a big problem for me, I have been extremely nervous lately waiting for one to crash due to excessive fragmentation. After finding out that ext3 doesn't need to be defrag'ed I can relax.
The more I use Ubuntu and the more I read about it the more I like it. Out of 2 laptops and 3 desktops I now only have one with Vista just in case I run into a situation where I absolutely have to have windows, otherwise I only use Ubuntu now and my computer problems are considerably fewer. I even have my wife using it.

thanks for the info.

drlmg

---

