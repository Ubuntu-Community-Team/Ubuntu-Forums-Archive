---
title: "[SOLVED] Backing up ubuntu"
date: 2008-11-19
forum: New to Ubuntu
---

### Post by Sarmacid on 2008-11-19
I was wondering if I can make a back up of ubuntu just by copying the / folder to a dvd and then restore it using a live cd, or maybe someone knows of a tool like dd but skips unused disk space and can tell me about it.

---

### Post by rampageoberon on 2008-11-19
You can use Remastersys or PartImage to make a copy of your system

[http://www.dedoimedo.com/computers/remastersys.html](http://www.dedoimedo.com/computers/remastersys.html)

---

### Post by Sarmacid on 2008-11-19
Thanks, I'll give that a try and get back to you.

---

### Post by Dedoimedo on 2008-11-19
> **rampageoberon said:**
> You can use Remastersys or PartImage to make a copy of your system

[http://www.dedoimedo.com/computers/remastersys.html](http://www.dedoimedo.com/computers/remastersys.html)

Thanks!

BTW, Sarmacid, you can also use imaging software, PartImage (meintioned) or CloneZilla. Both run from live CDs. I have tutorials for those too.

Dedoimedo

---

### Post by Sarmacid on 2008-11-19
Remastersys is working great, thanks a lot rampageoberon, and thanks Dedoimedo for the suggestions, but I still would like to know if just burning the file system onto a dvd would work.

---

### Post by rampageoberon on 2008-11-19
Thats excellent, well done for getting that sorted.

That is a kind of crude way to do it as you won't have any boot record etc and the system configurations in /fstab or /mtab might be different if you copy to another machine. So if you bakup to DVD and format the machine, then copy the files back, it will not work.

I do some mirroring but thats just my home folder. But to backup the system properly the method you just used is better.

---

### Post by Sarmacid on 2008-11-19
Just found out that restoring from a remastersys backup won't work cause I have no GUI. Guess I should have been more specific, I'm running Ubuntu server 8.04, without a gui. I will give the other options a try tomorrow maybe, can't spend more time in it today x_x

---

### Post by jimreynold2nd on 2008-11-19
Try this: [http://www.sysresccd.org/Main_Page]("http://www.sysresccd.org/Main_Page")
Download the liveCD, it defaults to CLI but if you want you can still do startx. And it comes with Partimage, OpenSSH, Samba, ntfs-3g (to backup to ntfs, NOT to backup an ntfs partition) as well as networking and scsi drivers.
I have been using it to backup my ubuntu once a week for 2 years now.
Some hint: Use gzip. Its fast and small. Just remember to **split** image file into 2GB pieces or else it wouldn't work.

---

### Post by rampageoberon on 2008-11-19
> **Sarmacid said:**
> Just found out that restoring from a remastersys backup won't work cause I have no GUI. Guess I should have been more specific, I'm running Ubuntu server 8.04, without a gui. I will give the other options a try tomorrow maybe, can't spend more time in it today x_x

Umm, what do you mean it won't work because you have no GUI. Please explain why in more detail. From what I understand it will install whatever system that you backed up so if it was server then server is what you'll get when you install from the livecd.

---

### Post by scorp123 on 2008-11-19
> **Sarmacid said:**
> I was wondering if I can make a back up of ubuntu just by copying the / folder to a dvd and then restore it using a live cd You will likely run into troubles when it comes to some special file permissions. ISO9660 and UDF (the file format CD's and DVD's get recorded in) has different structures than e.g. Ext3, ReiserFS, JFS or XFS (the most common Linux file systems). Hence I'd assume that it is not possible to copy files from a Linux installation onto a DVD _and_ have all the file permissions and special bits remain intact.

It would be better to compress stuff into tar.gz archives (or some other form of compressed images), just to make sure that the file structures and permissions inside stay intact, so everything incl. file permissions and any special bits get restored correctly when you unpack the archive again.

I personally use this method:
[http://www.linuxmint.com/forum/viewtopic.php?f=42&t=3969&start=0&st=0&sk=t&sd=a](http://www.linuxmint.com/forum/viewtopic.php?f=42&t=3969&start=0&st=0&sk=t&sd=a)

so I'd backup my stuff to external USB harddisks and then restore my stuff with the help of a Live CD off that USB harddisk again. With this I am not limited by the max. size of a CD or DVD and harddisks are more reliable too and usually big enough to really hold all your data + the kitchen sink ... which is usually not a bad thing. I'd rather have too much stuff in my backup and never need it than need too much stuff from my backup and not have it anywhere ... ;)

---

### Post by rugbeeprop on 2008-11-19
Hi,

Is there anyway to only backup the theme?

I term of data and documents, I store them in a completely different partition, so they are safe. I don't mind reinstall the system as each reinstall, comes new learning experience.

The only thing that I would like is that after the reinstall, I could have the exactly same theme that I had.

---

### Post by rampageoberon on 2008-11-19
I use mirrordir to backup my home folder. It just does a one way syncing of the folder specified.

```
sudo aptitude install mirrordir
mirrordir /path/to/dir /path/to/backup
```

Is that what you are looking for? hope it helps

---

### Post by jimreynold2nd on 2008-11-19
> **rampageoberon said:**
> Umm, what do you mean it won't work because you have no GUI. Please explain why in more detail. From what I understand it will install whatever system that you backed up so if it was server then server is what you'll get when you install from the livecd.

I think he meant he has no X-capable terminal, or he just wants to do it all from command line (via SSH or something like that).

---

### Post by rampageoberon on 2008-11-20
> **jimreynold2nd said:**
> I think he meant he has no X-capable terminal, or he just wants to do it all from command line (via SSH or something like that).

that is still possible, there's a config file which can be edited and remastersys has command line switches. think its 'remastersys dist' and over ssh it can always be run in a screen session

hope that helps

---

### Post by Sarmacid on 2008-11-20
> **rampageoberon said:**
> Umm, what do you mean it won't work because you have no GUI. Please explain why in more detail. From what I understand it will install whatever system that you backed up so if it was server then server is what you'll get when you install from the livecd.

Well, at first I thought it was ok running remastersys from CLI, even tho every time I did it it tried to download some packages for graphic interface, said they were installed and continued anyways. I did the backup and burned the CD to verify the backup would work I did something I believe many people want to too, cd / && rm -rf *. After that I put in the CD, cut the power and give it power again. It worked fine when I tried the live CD mode, I was just checking, then I rebooted and went for install. It started to load as if it was the live CD, no problem there, but then it hung at loading ubiquity, then it said failed to load x and dropped me to the same terminal as with the live CD.

After a bit of searching, I found out this [http://ubuntuforums.org/showthread.php?t=81311](http://ubuntuforums.org/showthread.php?t=81311) which worked perfectly, backing up and restoring. Thanks everyone for their help and concern.

---

### Post by rugbeeprop on 2008-11-20
A couple of questions:
1. If I restored using your method (mirrordir), would I have the theme I have setup?
2. Can the path be other hard drive?
3. What's the difference between using mirrordir and to manually copy the home directory somewhere else?


Thanks

---

### Post by rampageoberon on 2008-11-21
> **rugbeeprop said:**
> A couple of questions:
1. If I restored using your method (mirrordir), would I have the theme I have setup?
2. Can the path be other hard drive?
3. What's the difference between using mirrordir and to manually copy the home directory somewhere else?


[LIST=1]
[*]Okay this is assuming the theme config is stored in your home directory and is unique to you, (Or if its in another directory and you know where it is thats excellent) then **yes** you will get it back on restore.
[*]**Yes** you can use an external drive or flash drive etc. This is exactly what I do with my backups. I just mirror my home directory.
[*]mirrordir only copies over files that have changed or been updated, so is faster and more economical than a manual copy and paste. But essentially with new/modified files it will just be copying and pasting.
[/LIST]

Hope that answers your questions. If in doubt do ask :)

---

### Post by rugbeeprop on 2008-11-22
Thanks rampageoberon.

It makes sense now. So, I can just do manual copy and it would still work, instead of using mirrordir.

---

### Post by rampageoberon on 2008-11-23
> **rugbeeprop said:**
> Thanks rampageoberon.

It makes sense now. So, I can just do manual copy and it would still work, instead of using mirrordir.

Yes you can do a manual copy if you want to handle it this way. Hope thats enough info for you to decide what method to use

---

### Post by rugbeeprop on 2008-11-23
Excellent. Thanks for your help.

---

