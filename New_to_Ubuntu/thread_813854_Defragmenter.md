---
title: "Defragmenter?"
date: 2008-05-31
forum: New to Ubuntu
---

### Post by G!zZm0 on 2008-05-31
Isn´t there a defragmenter for Ubuntu so that I can compress my files???

---

### Post by ajmorris on 2008-05-31
a defragmenter? Linux file systems are journaled filesystems, meaning they do not need to be defragmented. There are defraggers you can get for ext3 systems, but unless you have mucked things up majorly, you dont need it.

AJ

---

### Post by hyper_ch on 2008-05-31
a defragementer does not compress files. a defragmenter "optimizes" the location of the files on the harddisk... a defragementer is not needed onl linux.

---

### Post by Blackmag+c on 2008-05-31
don't think linux partitions fragment :/ might be wrong though.

---

### Post by ajmorris on 2008-05-31
> **Blackmag+c said:**
> don't think linux partitions fragment :/ might be wrong though.

Yes that is correct, linux, and OS X for that matter, use what are called journaled file systems, because they are journaled, they do not fragment.

---

### Post by hyper_ch on 2008-05-31
ntfs is also journaled and fragementation happens there ;)

---

### Post by scorp123 on 2008-05-31
> **ajmorris said:**
>  Linux file systems are journaled filesystems, meaning they do not need to be defragmented.  Journalling has nothing to do with fragmentation ;)

A journal helps keeping your data's integrity intact because the journal will be able to tell your system what data indeed did get saved shortly before e.g. a power failure happened and what data did not get saved. A journal has no connection whatsoever to a file's fragmentation ... if a file fragments or not is entirely up to the filesystem in use, e.g. filesystems such as Ext3, XFS, JFS and many others from commercial UNIX vendors (UFS, ZFS, VxFS, etc.) try really really hard to avoid fragmentation by reserving enough space for a file so it's easy to add more and more to it later. Microsoft filesystems such as FAT32 or NTFS have no such strategy at all: dumb as they are they place files next to each other (first comes, first saved) and when you add more things to a file the file will have to be fragmented when and if the adjacent space is already occupied by something else.

Again ... this has nothing to do with the journal. ;)

---

### Post by Sef on 2008-05-31
About every 25 - 30 reboots, ext 3 will do a disk check that will attend to any defragmentation.  Fragmentation is not a problem with it, unless your disk is about 90% full.

Reifersfs does not defragment at all.

---

### Post by ajmorris on 2008-05-31
> **hyper_ch said:**
> ntfs is also journaled and fragementation happens there ;)

NTFS is not journaled

---

### Post by scorp123 on 2008-05-31
> **hyper_ch said:**
> ntfs is also journaled  Only partially if I interpret Wikipedia correctly:

[http://en.wikipedia.org/wiki/Ntfs#Internals](http://en.wikipedia.org/wiki/Ntfs#Internals)
>  ".... Internally, NTFS uses B+ trees to index file system data. Although complex to implement, this allows faster file look up times in most cases. A file system journal is used to guarantee the integrity of the file system—but not individual files' content ... "

So even though NTFS does have a journal a sudden power failure might have a good chance to ruin whatever file you were working on because NTFS doesn't care about keeping your files' contents intact.

How "nice" .... :)

---

### Post by el-mar01 on 2008-05-31
So Ubuntu/Linux has a more advanced file system than Windows ??

---

### Post by ajmorris on 2008-05-31
> **scorp123 said:**
> Journalling has nothing to do with fragmentation ;)

A journal helps keeping your data's integrity intact because the journal will be able to tell your system what data indeed did get saved shortly before e.g. a power failure happened and what data did not get saved. A journal has no connection whatsoever to a file's fragmentation ... if a file fragments or not is entirely up to the filesystem in use, e.g. filesystems such as Ext3, XFS, JFS and many others from commercial UNIX vendors (UFS, ZFS, VxFS, etc.) try really really hard to avoid fragmentation by reserving enough space for a file so it's easy to add more and more to it later. Microsoft filesystems such as FAT32 or NTFS have no such strategy at all: dumb as they are they place files next to each other (first comes, first saved) and when you add more things to a file the file will have to be fragmented when and if the adjacent space is already occupied by something else.

Again ... this has nothing to do with the journal. ;)

Yes, what i meant was that UNIX vendors as you put it, use journal for their strategies. It tells the system what was saved before it, so they dont get put directly next to each other

---

### Post by scorp123 on 2008-05-31
> **ajmorris said:**
> NTFS is not journaled It is partially ... see my posting above this one.

But yes, NTFS' "journalling" if one can even call it like that seems to be sub-standard from the Linux POV.

---

### Post by ajmorris on 2008-05-31
> **el-mar01 said:**
> So Ubuntu/Linux has a more advanced file system than Windows ??

If you would like to put it like that, yes

---

### Post by ajmorris on 2008-05-31
> **scorp123 said:**
> It is partially ... see my posting above this one.

But yes, NTFS' "journalling" if one can even call it like that seems to be sub-standard from the Linux POV.

Yeah, its not proper journalling

---

### Post by scorp123 on 2008-05-31
> **ajmorris said:**
>  Yes, what i meant was that UNIX vendors as you put it, use journal for their strategies.  Again no. Please read again: The journal's purpose is only to make sure the filesystem knows what happened  shortly before an unexpected event such as an immediate power failure, so it knows which files are OK and which files went to the digital Nirvana because its contents could not be saved shortly before the power failure happened.

Example: 

You're working on two files in OpenOffice. "Example1.odt" and "Example2.odt". You save the first file ... your harddisk blinks for a few seconds, and everything is fine. You save the second file, the harddisk starts blinking ... and now the power fails!

You reboot again and your system is checking what in the world just happened. And during it's filesystem checks it will run across the files you were working on .... "Example1.odt ... hmmmmm, did I have time to save that one? According to the time stamps: yes. And according to the journal: Yes, as well. OK, this file is intact. Nothing to do here ... "

Then it will run across the second file:

"Example2.odt .... Hmmmmm. Is this intact? Time stamps say: yes. And the journal: heck, NO! According to the journal this file was still in the process of being written to when the crash happened. Uh oh! We have a corrupt file! Damn, I gotta notify my user and ask him if he wants me to attempt a repair ......."

> **ajmorris said:**
>  It tells the system what was saved before it, so they dont get put directly next to each other  The placement of files has nothing to do with the journal!

Ext2 wasn't journalled and yet fragmentation was hardly ever an issue! Same goes for other UNIX filesystems such as e.g. UFS! There are still many many thousands of servers out there which use UFS in a non-journalled version and yet fragmentation is not an issue there ;)

As I said: the filesystem journal has nothing whatsoever to do with fragmentation, OK? ;)

---

### Post by articpenguin on 2008-05-31
NTFS journals what ext3 journals metadata only. So the only filesystem metadata is always in a consistent state not user files.

---

### Post by airtonix on 2008-06-02
there was a great short explanation with diagrams about how the two system di this file placement...can't find it though.. :(

---

### Post by kwacka on 2008-06-02
This is the clearest, simple explanation that I've seen:
[http://preview.tinyurl.com/hlr99](http://preview.tinyurl.com/hlr99)

(At the "http://geekblog.oneandoneis2.org" sites).

---

### Post by scorp123 on 2008-06-02
> **kwacka said:**
> This is the clearest, simple explanation that I've seen:
[http://preview.tinyurl.com/hlr99](http://preview.tinyurl.com/hlr99)

(At the "http://geekblog.oneandoneis2.org" sites). You rule! :) I was looking for that URL but couldn't find it anymore for the life of me :)

Thanks for posting it :)

---

### Post by chuckh1958 on 2009-09-03
I know this is a year old thread but I thought I'd ask a question or two anyway.

Why does the fact that a file system is journaled mean that it does not get fragmented? I thought [journaling]("http://en.wikipedia.org/wiki/Journaling_file_system") simply meant that changes to blocks are tracked, primarily to prevent corruption in the event of a crash or power failure. If thats the case then journaling and fragmentation are unrelated. 

My understanding of linux file systems (I use ext3) is that they purposely fragment files - or rather distribute the blocks of a file over the free space of a disk, rather than using the Microsoft approach of trying to store all blocks contiguosly. So in that sense the files are actually always fragmented.

Am I misunderstanding something here?

---

### Post by philinux on 2009-09-03
Journaling and fragmentation have nothing in common.

The thing is ext3 file systems do fragment but it is only noticeable if you a running large servers with very large files.

When fsck runs it does not defrag but it does report how much fragmentation there is.

---

### Post by sydbat on 2009-09-03
> **chuckh1958 said:**
> I know this is a year old thread but I thought I'd ask a question or two anyway.

Why does the fact that a file system is journaled mean that it does not get fragmented? I thought [journaling]("http://en.wikipedia.org/wiki/Journaling_file_system") simply meant that changes to blocks are tracked, primarily to prevent corruption in the event of a crash or power failure. If thats the case then journaling and fragmentation are unrelated. 

My understanding of linux file systems (I use ext3) is that they purposely fragment files - or rather distribute the blocks of a file over the free space of a disk, rather than using the Microsoft approach of trying to store all blocks contiguosly. So in that sense the files are actually always fragmented.

Am I misunderstanding something here?Yes you are. You have switched the ideas around. 

Linux file systems allocate large blocks so files are not fragmented and leave room for those files to be added onto (expanded). 

Windows file systems put files right next to each other and do not leave room for expansion. When you add anything to those files, it is placed in the first available slot. Only after a defrag session are Windows files put back together. Also, if you delete a file, that space becomes the "first available" and if it is not large enough to store whatever you want to save, it will split it up (fragment it).

This link from a few posts back explains this much better - [http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting](http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting)

---

