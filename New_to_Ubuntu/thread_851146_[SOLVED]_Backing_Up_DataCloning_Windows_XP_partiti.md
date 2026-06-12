---
title: "[SOLVED] Backing Up Data/Cloning Windows XP partition"
date: 2008-07-06
forum: New to Ubuntu
---

### Post by Lazy-buntu on 2008-07-06
My family member is planning on buying a 500GB external hard drive to back up data and they want me to help them.


She is having computer problems with her HP laptop with Windows XP (since she didn't want to listen to my tips or switch to/dual boot a linux distro), so now she has decided to restore the laptop to factory settings.

After restoring the laptop to the factory settings, and putting all her backed up data back on the laptop, she wanted to make a restore point of sorts--so the next time (if she has to) restore the computer, she can restore it to this point. Basically, a fresh install with her data on there. 


I was wondering how I could do this for her. I was thinking of a hard drive cloning software for her OS partition, but I'm not sure. In other words I would partition the 500GB hard drive so that 40GB (or whatever size) would be the cloned image of that partition, then go from there.

Would this work? If so, what do you guys recommend for free hard drive cloning software and partitioner? I was thinking just GParted for partioning, but I don't know any good cloning software.

Also, what's the fastest way to backup data to the external hard drive? CTRL+C CTLR+V?

---

### Post by swisscow on 2008-07-06
I back up my linux partitions onto an external USB drive by booting into the SYS Rescue CD (can be downloaded) and then running partimage.

This is one possible way of making a "restore point", sure there must be more. And it has the advantage of holding all data, settings, apps etc

---

### Post by bumanie on 2008-07-06
You could make an exact copy with gparted, but it will not compress - it is that exactly, a copy. The other things you could use are dd commands that will compress with gzip, partimage live cd which is basically a graphical version of dd. There is also ghost4linux and a number of other tools you can find information about on the internet. Personally I'd use dd commands, but you may prefer something with a gui. There is also ntfsclone which is available in the ntfsprogs tools available from the ubuntu repositories - not sure if that compresses, but you  may be able to gzip it after the 'cloning' process - you would have to read the documentation to make sure.

---

### Post by Lazy-buntu on 2008-07-06
I think I've got SYSrescue CD somewhere, I know I have trinity rescue cd...I pop both in my laptop real quick. 

Side question: are there any utilities you can run from within Windows XP? Chances are, if I try cloning the partition with a live CD she'll start freaking out and tell me to stop lol.

edit: I've got both SYSrescue CD and trinity

---

### Post by bumanie on 2008-07-06
Trinity rescue disk kit has ntfs clone on it as far as I remember - or at lest something that does the same job. Yes. You do need to copy/clone a partition that is not mounted, otherwise you a likely to get some unstable data transferred. System rescue cd has partimage. I'd go for TRK, but that's up to you. Both sites where you get the discs have some documentation, it's not brilliant, but better than none at all!

---

### Post by Lazy-buntu on 2008-07-06
I was thinking: [http://lifehacker.com/software/geek-to-live/partition-and-image-your-hard-drive-with-the-system-rescue-cd-292972.php](http://lifehacker.com/software/geek-to-live/partition-and-image-your-hard-drive-with-the-system-rescue-cd-292972.php)

It's from Fri Aug 24 2007, so I'm guessing it's not outdated. Does this seem like a reasonable how-to?

---

### Post by Lazy-buntu on 2008-07-06
Any one have experience with Clonezilla? It looks like it would be the most simple way to copy the entire hard disk over, but I can't find out whether or not it could work with an external USB hard drive.

edit: [http://goinglinux.com/articles/ClonezillaLive.html](http://goinglinux.com/articles/ClonezillaLive.html)

---

### Post by bumanie on 2008-07-06
Clonezilla or any tool based on linux should copy to an external hard drive without issue, as linux sees everything as a files. A device such as an external hard drive is a file on the 'tree' under root. (Personally never got clonezilla to work, but many have). As I said in the original post re this issue there are many linux-based tools to accomplish what you are wishing to do. You have to read up on them and decide which to try and whether you need a compressed image or not. At the end of the day, many are built on the same underlying tools, whichever tool you choose - you need to use one you are comfortable with or build a virtulal environment to test the various tools before trying on the real discs.

---

### Post by Lazy-buntu on 2008-07-06
Okay. Thanks for the guidance. I've been looking in to Clonezilla, and I think I'll try that out given the chance to clone the hard drive. But knowing the person who needs it done, I'm sure she'll find an excuse to ignore my help :confused:

It's annoying how often she needs help with her computers, but how unwilling she is to listen to my advice. I can't even get her to try out Firefox :lolflag:

---

### Post by Lazy-buntu on 2008-07-12
Clonezilla didn't work for me, and sysrescue CD wouldn't even boot on her laptop.

I ended up using Norton Ghost 14.0, which worked perfectly fine :)

---

