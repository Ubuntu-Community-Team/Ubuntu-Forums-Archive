---
title: "Read the header of a disk sector"
date: 2013-03-23
forum: Programming Talk
---

### Post by magmaman42 on 2013-03-23
Hello,

I'm looking for a low-level linux program that I can use to read the header of a disk sector.  I have an idea that dd might do it, but I'm not sure and I've been googling for a while.  I'd like to be able to read the various pieces of information in that header: address identification, header parity bytes, etc.

Also, will my ability to do this be affected by the type of file system I use?  e.g., a journaling file system or otherwise?

Thanks!

Mag

---

### Post by matt_symes on 2013-03-23
Hi

> **magmaman42 said:**
> Hello

Welcome to the forums :)

> 
I'm looking for a low-level linux program that I can use to read the header of a disk sector.  I have an idea that dd might do it, but I'm not sure and I've been googling for a while.  I'd like to be able to read the various pieces of information in that header: address identification, header parity bytes, etc.

If i understand you correctly.....

I think most of this is handled by the drives firmware and, therefore, is proprietary. 

I'm not sure if dd will do the job here. 

I'm not sure if it will get the ECC parity information and sector addresses you are after as this information wraps the sector.

I believe dd will just pull the information from the/a sector it is currently looking at without the header and parity information. (I am open to correction here though).

> 
Also, will my ability to do this be affected by the type of file system I use?  e.g., a journaling file system or otherwise?

Thanks!

Mag

If you can find a tool to do the job your require then it should be file system independent as this is at a very low level indeed on the platters and is the information that wraps the sectors telling the drives firmware where the sectors are and the ECC checksum for error correction.

I'm intrigued and i am also Googling to see if there is some software you can use under Linux.

I'll post back if i find any.

Kind regards

---

### Post by magmaman42 on 2013-03-24
Hi Matt,

Thanks for your input and your welcome.  :)

I've been doing some searching (and have been experiencing a pretty steep learning curve), and finally found this thread: [http://www.forensicfocus.com/Forums/viewtopic/t=9325/postdays=0/postorder=asc/start=7/](http://www.forensicfocus.com/Forums/viewtopic/t=9325/postdays=0/postorder=asc/start=7/).  The last post pretty much clears up the question.  I can't read that data; not unless I were to find drive model-specific software.  I was hoping to do something more drive-agnostic.

I'm wondering, though, if I'll be able to do this with blocks of data...the program badblocks seemed a pretty good start.  If I need help I'll start a new thread.

Thanks!

---

### Post by schragge on 2013-03-24
I'm not quite sure what you mean with blocks of data, but I guess [dd](http://manpages.ubuntu.com/manpages/precise/en/man1/dd.1.html), or on a lower level, [hdparm --read-sector](http://manpages.ubuntu.com/manpages/precise/en/man8/hdparm.8.html) would do the job. *axi-cache search* also gives me [blktool](http://manpages.ubuntu.com/manpages/precise/en/man8/blktool.8.html), *scsitools* and [sg3-utils](http://sg.danny.cz/sg/sg3_utils.html) as packages similar in function to hdparm, but I never used them. Yet some tools from [sg3-utils](http://manpages.ubuntu.com/manpages/precise/en/man8/sg3_utils.8.html) like [sg_dd](http://manpages.ubuntu.com/manpages/precise/en/man8/sg_dd.8.html) and its variants look promising.

---

### Post by magmaman42 on 2013-03-28
Hey Schragge, thanks for the ideas.  I'll look into them.  Don't think  that dd will be able to read what I'm looking for, but I wonder if  there's some way I can delve into the inner workings of the other tools  you mentioned...maybe learn how to write a variation on one of them.    (At least I have a couple of junk HDDs lying around.)  :-D

'Blocks of data'...from what I understand, I was referring to the organizational structure of an HDD, where sectors are grouped into blocks.  Am I mistaken?  I've seen the terms used interchangeably on a couple of related man pages.

Thanks!

---

### Post by oldfred on 2013-03-28
Sectors are the blocks of data on a drive.
But drives are organized by types of partitioning, currently MBR(msdos) or gpt(GUID) for most PCs.
       MBR details including 2TiB limit and GPT link
[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)
Windows does not follow UEFI spec on size of protective MBR (starman's site has a lot of technical detail)
[http://thestarman.pcministry.com/asm/mbr/GPT.htm](http://thestarman.pcministry.com/asm/mbr/GPT.htm)

    
Then within each partition is the format which can be many different types of formats, ext2, ext3, ext4, NTFS etc.

Not sure what you want to see?

---

