---
title: "how to do a defrag in UBU"
date: 2008-10-27
forum: New to Ubuntu
---

### Post by bu2971x on 2008-10-27
how do you do this??

---

### Post by StOoZ on 2008-10-27
no need to...

---

### Post by eolson on 2008-10-27
+1 ... the Ubunto file system does not require it.   One more thing you don't need to worry about.

---

### Post by nhasian on 2008-10-27
i dont think you need to defrag ext3 paritions but if your so inclined you can use shake:

[http://vleu.net/shake/](http://vleu.net/shake/)

---

### Post by em4r1z on 2008-10-27
Depending on your filesystem, there may be a defragmentation tool. Assuming you use ext3, read this:
[http://en.wikipedia.org/wiki/Ext3#Defragmentation](http://en.wikipedia.org/wiki/Ext3#Defragmentation)

---

### Post by sparvik on 2008-10-28
Will shake defrag an external HDD that is in FAT32 or another Windonts file system format?

---

### Post by nhasian on 2008-10-28
oh you want to defrag a fat32 filesystem?  its probably safest to do that in windows.  I dont know how large your usb drive is or how much data is on it, but another way to defragment it is to copy all the data off of it, reformat it and then copy the data back.

---

### Post by Crafty Kisses on 2008-10-28
You don't really have to defrag in Linux, the file system is organized and stored more efficiently than a Windows box. If you really want to then I can
suggest you go to something like Google and search "Linux defrag" or something and grab a utility, they do exist, but unnecessary.

There is an option to "clean" though, just run this command in terminal:
```
sudo apt-get clean
```

---

### Post by gvoima on 2008-10-28
Yes, there's no need to defrag a journaling filesystem. So don't worry :)

---

### Post by jerome1232 on 2008-10-28
edit: Did some more reading up on file systems, ext3 defrags on the fly and such :)

---

### Post by Sef on 2008-10-28
>  				 				**how to do a defrag in UBU** 			
 			 			 		   		 		 		how do you do this??


After 25 or 30 times, it will automatically defrag the hard drive.

---

### Post by charliebrownau on 2008-10-28
Is there a way to Defrag FAT32 and NTFS drives
 in Linux without taking the Drives/Partitions/USB out
 or booting into Windows ?

 FAT32 and NTFS comes in handy for file sharing and
 when you have Duel OS situation .

 (Sure if you have Win and Linux you could reboot 
  into windows just to defrag but it would be handy
  to stay in Linux and defrag )

---

### Post by crazyness003 on 2008-10-28
> **charliebrownau said:**
> ... Defrag ... NTFS drives
 in Linux without ... booting into Windows ?

 FAT32 and NTFS ... for file sharing ... Duel OS ...

... would be handy
  to stay in Linux and defrag )

Seconded. Thats what makes Linux OVER9000 times better than win. It can [almost] support NTFS with no support from 3rd party.

In win you can only read ext2 partitions using some program (forgot what it was called).

---

### Post by sparvik on 2008-10-28
> **charliebrownau said:**
> Is there a way to Defrag FAT32 and NTFS drives
 in Linux without taking the Drives/Partitions/USB out
 or booting into Windows ?

 FAT32 and NTFS comes in handy for file sharing and
 when you have Duel OS situation .

 (Sure if you have Win and Linux you could reboot 
  into windows just to defrag but it would be handy
  to stay in Linux and defrag )

This was the question I was Asking, and very handy if you have a lot of video's you want to carry to a friends house.

---

### Post by Paqman on 2008-10-28
> **charliebrownau said:**
> Is there a way to Defrag FAT32 and NTFS drives
 in Linux without taking the Drives/Partitions/USB out
 or booting into Windows ?

 FAT32 and NTFS comes in handy for file sharing and
 when you have Duel OS situation .


Not as far as I know. This is one of several good reasons to use NTFS instead of FAT32 for sharing. NTFS gets a lot less fragmented.

---

### Post by sparvik on 2008-10-29
I've done a bit of research into this and apparently quit a few posts have been made on this subject.  I've searched numerous forums for Linux and they all come to the same conclusion.  Nobody in the Linux community that has had the expertise to program a dfrag, has really felt the need to build one for a fat32 or any other non-Linux file system. So if people like us want one we will have to build it ourselves. 

I found a command line utility that might work but it is said that it is most likely to destroy most of the data anyways so I didn't save the page.

This looks like a closed issue until one of us who wants it learns the skill to make it.

---

### Post by crazyness003 on 2008-10-30
but there isint really a demand for it. Linux should use ext3, and if you even have NTFS that means you have windows installed. just use the OS for the FS it was designed for.

It would be nice to have an ntfs defragger for Linux, but not necessary.

---

### Post by igknighted on 2008-10-30
> **crazyness003 said:**
> Seconded. Thats what makes Linux OVER9000 times better than win. It can [almost] support NTFS with no support from 3rd party.

In win you can only read ext2 partitions using some program (forgot what it was called).

There are several windows drivers to mount and read/write ext3 partitions natively.  I don't think there's any need for a fat32 or even ntfs sharing partition.

---

### Post by jerome1232 on 2008-10-30
> **igknighted said:**
> There are several windows drivers to mount and read/write ext3 partitions natively.  I don't think there's any need for a fat32 or even ntfs sharing partition.

They read/write to ext2, there's a difference ext2 has no journal, ext3 does. fat has no journal, ntfs does.

---

### Post by crazyness003 on 2008-10-31
> **igknighted said:**
> There are several windows drivers to mount and read/write ext3 partitions natively.  I don't think there's any need for a fat32 or even ntfs sharing partition.

As dude above me stated, ext2 is readable. Haven't tried write, and dont intend to. Anything windows touches turns to ashes. The only reason why fat and ntfs haven't turned to ash is because they are ash, just ready to vanish in a slight breeze. 

As for the need to share ntfs, yes there is: I already have >1.5 tb of data on NTFS drives and would be a very cumbersome and risky manuver to convert to anything else, plus, windows is teh suxor at handling Linux partitions. so im not gonna do something that will jeopardize my docs. And since 1/2 my family insist on using win (with 1 member using osx), i have [almost] no choice but to support it.

If you can direct me to the ext3 r/w drivers for win, i might give them a try, but its almost a lost cause. Until all OS's use a standard (and i mean a real standard) its gonna be a pain to support all platforms. So i have an idea:
[COLOR=Red][B]


BRING BACK THE FLOPPY[/B][/COLOR]
Any platform can support, read, write and share floppy! w00t floppy, ftw!

---

### Post by theDaveTheRave on 2008-11-07
I have a similar question to this.

I have an external HDD that a colleague was using as a backup device, 
I was contemplating doing a similar thing for my important files (but not concerned about the OS as I can easily re-install:guitar:

However I want to partition the disk, so as I can then have a linux partition on it and run linux from this disk on other terminals with all my settings / files etc, and even maybee use it as a means to install ubuntu on other systems?

Well I have the disk and I have run the windows defrag utility on it (from the windows desktop at work). but the graphic in windows shows a large amount of "white space" rather than a single large block of data at the "front" of the external drive.

I remember using an nortons utility tool many years ago that seemed to be much better at defragmentation than the windows thing that is supplied as standard.

can anyone advise of a tool that will give me the desired result of a single large patch or free space.

thanks in advance.

David

---

### Post by psusi on 2008-11-07
> **Codename said:**
> You don't really have to defrag in Linux, the file system is organized and stored more efficiently than a Windows box. If you really want to then I can
suggest you go to something like Google and search "Linux defrag" or something and grab a utility, they do exist, but unnecessary.

There is an option to "clean" though, just run this command in terminal:
```
sudo apt-get clean
```

It has nothing to do with the filesystem, it has to do with allocation policy.  Likewise, journaling has nothing to do with fragmentation.  The Linux kernel is much smarter about picking where to start writing files on disk such that they have room to grow without becoming fragmented.  Microsoft has always liked to just find the first free block on the disk, even if there are no more free blocks immediately after it.

Because of this, Linux keeps fragmentation to a minimum, but it does still happen, especially on long lived very full disks.

Also apt-get clean has NOTHING to do with disks or fragmentation; it just removes any packages you have recently installed from the apt cache.

pyfragtools is a package that will try to reduce fragmentation by copying badly fragmented files until they have fewer fragments.  It should work on any filesystem.

The old defrag package for ext2/3 was removed two releases ago because it had not been maintained in so long.  I am trying to bring it back so those who really want to can run an old school full filesystem offline defrag.

---

### Post by oldos2er on 2008-11-07
> **Sef said:**
> After 25 or 30 times, it will automatically defrag the hard drive.

 Don't you mean to say, it will run fsck? fsck isn't defragging.

---

### Post by psusi on 2008-11-07
> **oldos2er said:**
> Don't you mean to say, it will run fsck? fsck isn't defragging.

Ahh, forgot to mention that myself...

---

