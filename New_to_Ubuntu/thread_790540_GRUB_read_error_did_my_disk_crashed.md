---
title: "GRUB read error: did my disk crashed?"
date: 2008-05-11
forum: New to Ubuntu
---

### Post by a_rojilla on 2008-05-11
Hi,

First of all excuse me for my poor english and specially for my close to zero knowledge about computers...

OK, here is the (long?) story:

A few years ago I bought a PC with 2 160GB HDDs and Windows XP installed by default. Both disks were used as one (320GB) and when I later installed OpenSUSE used one of those disks so I ended up with XP in the master (/dev/hda) and OpenSUSE in the secondary disk (/dev/hdb) with 3 partitions.

Everything's been running fine, and over the time I stopped using XP and have been giving a try to other distribuions like Ubuntu. I liked it and installed Ubuntu in my laptop (the one I using to write this) where I finally removed Windows :)

I was ready to format my desktop PC and install Ubuntu as my only OS (I like OpenSUSE a lot, but I like Ubuntu even more, specially for the wide community support everywhere and the easy upgrading process -I'm using 8.04 right now-). I've been backing up all my important files these past days (writing them on DVDs and some flash memories) but still had some left when...

Yesterday, all of a sudden, when I switched my desktop PC on all I got was a

```
GRUB: read error
```

That's all. All I can do is press Ctrl+Alt+Del to get the same error again and again.

So I tried to run Ubuntu 7.10's Live CD to see what was wrong or what could I do and all I could get was an endless list of 

```
BUFFER I/O ERROR ON DEVICE HDA LOGICAL BLOCK O
```

or something like that (right now I'm writing just what I can remember). There was a lot of numbers with every of those lines I was getting... too much to make sense to me...

Anyway, I tried later with an 'old' Ubuntu 6.06's Live CD (the first I used to try out Ubuntu) with succes and the first thing I did was to run GParted: I could see both disks (hda -XP- and hdb -OpenSUSE-) but while hdb showed as expected (I can see the 3 partitions -2 ext3 and 1 swap- with all the used and free space) hda shows just like a big empty gray colored **unallocated** space... What does this mean? Is it completely gone?

I've also tried some commands like fdisk, fsck...

With **fdisk -l** only the 3 hdb partitions are listed: nothing about hda.

With **fdisk /dev/hda** I get

```
Unable to read /dev/hda
```

**fsck /dev/hda** returns

```
Attempt to read block from filesystem resulted in short read while trying to open /dev/hda
Could this be a zero-length partition?
```

**fsck /dev/hda1** gives me

```
No such file or directory while trying to open /dev/hda1

The superblock could not be read or does not describe a correct ext2 filesystem. If the device is valid and it really contains an ext2 filesystem (and not swap or ufs or something else), then the superblock is corruct, and you might try running e2fsck with an alternate superblock: e2fsck -b 8193 device
```

Same for e2fsck and/or for /dev/hda2...

So... what does all this mean? Any idea of what to next? Should I just run the Ubuntu installer from the CD, format both disks and forget about all of this? Or will be this plain stupid because one of the disks is allready broken? Any idea?

To sumarize, **these are my main questions**:

**1**.- Is there a way to use the Ubuntu's Live CD to restore GRUB and be able to acces my PC as allways so I can back up the few things left?

**2**.- If not possible to restore GRUB... can I simply format the disks and install Ubuntu or will the disk problem prevent me from doing this?

**3**.- Is is a software or hardware problem? Should I just ditch the disk?

Thanks in advance for your time and any help or suggestions.

PS: I've spent the last 5 or 6 hour trying to find a solution trough search engines... with no luck... Sorry if this has been allready posted here (and/or if this not the propper forum).

---

### Post by JerMe on 2008-05-11
Sounds like the drive is hosed. :(  Try using [DBAN]("http://dban.sourceforge.net/") to wipe the drive before throwing it out.  I doubt it'll go through, but might as well give it as shot.  Good luck.

---

### Post by RJARRRPCGP on 2008-05-11
> **JerMe said:**
> Sounds like the drive is hosed. :(  Try using [DBAN]("http://dban.sourceforge.net/") to wipe the drive before throwing it out.  I doubt it'll go through, but might as well give it as shot.  Good luck.

I agree. Because a Maxtor 6E040L0 I had caused the dreaded  "Buffer I/O error in X" message repeating.

I think the HDD hardware cache has kicked the bucket.

I think that probably was a bad HDD, because, folks at hddguru.com seem to commonly have problems with Maxtor 6E0xxxx HDDs.  

Maxtor 6E0xxxx apparently are unpredictable when they fail. 

Maxtor 6E0xxxx s seem to develop a problem where it's fine then they start acting strange:

The most likely strange behaviors of Maxtor 6E0xxxx to occur are:

1. You notice stuttering (many short pauses) when scanning the HDD.

2. The HDD takes a long time to get ready. 

3. Then the HDD suddenly disappears from the BIOS. 

Folks at hddguru.com seem to commonly report firmware and PCB failure issues, thus, not majorly surprised about the hardware cache on the HDD having corruption.

If your Maxtor is model 6E030L0 or 6E040L0, just throw it away! 

Maxtor seems to have dropped the ball with these models. (Before Seagate acquired them)

---

### Post by a_rojilla on 2008-05-12
Well, obviously not the answers I was waiting for... :(

Time for a new HDD? Seems so...

Thak you so much for your time!

---

### Post by tacutu on 2008-05-12
I know it sound crazy, but did you try opening the case, unpluging, and re-pluging the HDD? Sometimes the craziest things happen, you might actually get it to work -- at least enough to backup your data.

also shaking and rattling (gently) the computer might help. I know from personal experience... :)

---

### Post by slira on 2008-05-12
Hi
to save your remaining files/folders you can access with an external boot (live cd or a DSL in a flash drive). You just have to mount the hdd (the one that is working) and copy the data. Then... reinstall from scrach! I hope it works
best

---

### Post by a_rojilla on 2008-05-15
> **tacutu said:**
> I know it sound crazy, but did you try opening the case, unpluging, and re-pluging the HDD?

Well, after the incident I have decided to update the PC with new RAM and a few other things, so while I am at it I'll try to do that and everything that comes to my mind. Let's see what happens...

Thank you so much to all!

Regards.

---

