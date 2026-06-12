---
title: "Why can Ubuntu read NTFS, but Windows can't in EXT2?"
date: 2011-09-10
forum: New to Ubuntu
---

### Post by Wiking on 2011-09-10
Hi, how come Ubuntu is able to read NTFS format hard drive for windows, and even move and modify files in that format, but Windows can't read the HD format that Ubuntu uses? 

I would like to have a better understanding if someone could explain. 

I sort of screwed up formatting my HD so Windows 7 can't read one of my HDs, but I will be transfering it to a NTFS formatted drive using Kubuntu.

I just want to understand how Ubuntu can both read and modify files in both formats while Windows only works in NTFS.

I shouldn't have any troubles transfering the files should I? 

I aplogize in advance for the noob question.

---

### Post by CharlesA on 2011-09-10
Windows uses NTFS cuz that's just what it uses. Linux uses EXTx, among others. That's just how it is.

You can try using a third party driver to read ext2, but I haven't used anything like that.

---

### Post by sarwiz on 2011-09-10
because windows really isn't that smart.

---

### Post by sarwiz on 2011-09-10
to add, I have extensively used gparted to resize and modify my partition tables on many different Hdds without an error, but the new partitioner in windows 7 totally screwed up a drive the first time I used it, fortunately on  blank drive, and that was the last time I used it.

---

### Post by Enigmapond on 2011-09-10
Windows hates competition...):P

---

### Post by haqking on 2011-09-10
> **Wiking said:**
> Hi, how come Ubuntu is able to read NTFS format hard drive for windows, and even move and modify files in that format, but Windows can't read the HD format that Ubuntu uses? 

I would like to have a better understanding if someone could explain. 

I sort of screwed up formatting my HD so Windows 7 can't read one of my HDs, but I will be transfering it to a NTFS formatted drive using Kubuntu.

I just want to understand how Ubuntu can both read and modify files in both formats while Windows only works in NTFS.

I shouldn't have any troubles transfering the files should I? 

I aplogize in advance for the noob question.

Microsoft is proprietary software and NTFS is there filesystem designed by Dave Cutler from DEC who created VMS who interestingly enough headed design on Windows NT or WNT, if you notice WNT is one letter each removed in the alphabet from VMS ;-) and HAL in 2001 was made by IBM, HAL is one letter removed from IBM...useless fact...LOL

anyways yes it is proprietary so they dont put any real effort into supporting other filesystems and the like.

Linux is open source with a global community of developers, the only restrictions to what it can do is whether someone contributes code to allow it to do it.  Linux developers decided Linux should be able to read from multiple filesystems and so it does, MS do not.

---

### Post by Enigmapond on 2011-09-10
> **haqking said:**
> Microsoft is proprietary software and NTFS is there filesystem designed by Dave Cutler from DEC who created VMS who interestingly enough headed design on Windows NT or WNT, if you notice WNT is one letter each removed in the alphabet from VMS ;-) and HAL in 2001 was made by IBM, HAL is one letter removed from IBM...useless fact...LOL

:lolflag:

---

### Post by haqking on 2011-09-10
> **Enigmapond said:**
> :lolflag:

Well always nice to throw a bit of history in there, you never know when you will need it for a pub quiz...LOL

---

### Post by Enigmapond on 2011-09-10
I totally agree..the world is full of useless facts...some are just more useless than others. Yours however shows real thought.. :)

---

### Post by haqking on 2011-09-10
> **Enigmapond said:**
> I totally agree..the world is full of useless facts...some are just more useless than others. Yours however shows real thought.. :)

I wont even go into the whole 42 thing being the default expiry for passwords in NT and windows 2000.

I am sure you can figure it out.

if you cant then, so long and thanks for all the fish LOL

anyways off topic.

Linux can do lots of things cos its development is open, MS cannot or do not because it is closed and proprietary !

---

### Post by Wiking on 2011-09-10
Thanks for the info guys. So since Snow Leopard is Linux based I'm guessing it can also read NTFS and EXT2 and other formats like Ubuntu?

---

### Post by papibe on 2011-09-10
Asking why Windows does or doesn't do this or that in a forum like this will give you all sort of answers. Some of them very entertaining.

Now about your concern. Here's a few ideas:
[LIST]
[*]Use a syncing service like Dropbox or Ubuntu One.
[*]Syncing to Win7's partition every time you are in Ubuntu.
[*]Create a shared NTFS partition, and use it as a working folder in Ubuntu (that way it always be availble in Windows)) .
[/LIST]
Note that in the last case, it can't be directly your home (/home/youruser) since Ubuntu won't be able to work very well.

I hope this helps,
Regards.

---

### Post by haqking on 2011-09-10
> **Wiking said:**
> Thanks for the info guys. So since Snow Leopard is Linux based I'm guessing it can also read NTFS and EXT2 and other formats like Ubuntu?

Ubuntu is not a filesystem it is a Linux Distro, which supports all the Linux filesystems such as ext2,ext3,ext4 etc etc

Mac OSX is originally based on FreeBSD UNIX, but yes i think it supports multiple filesystems.  Not sure though if it supports NTFS though, i think so ?

---

### Post by vanquishedangel on 2011-09-10
The answer I believe is that Microsoft doesn't want people to use other formats then there own. If people knew of better operating systems then they would use them, and with most users only knowing of Microsoft and only using Microsoft, Microsoft doesn't want them to know of others. essentially because if people were to use opensource formats or knew of them, they wouldn't pay for Microsoft formats. So if another format other than Microsoft's is found by a Microsoft user they will disregard it because they cannot use or read it and think that it is a deficient in the file.

However there is a program out there that does enable windows to read ext file systems you just gotta Google it and you will eventually find it.

---

### Post by haqking on 2011-09-10
oh and a final note.  As i mentioned previously, Dave Cutler from DEC who headed up the design team for Windows NT and onwards etc, openly HATES everything *Nix related and so that is probably a continuing reason for its lack of support.....LOL

---

### Post by Enigmapond on 2011-09-10
> **vanquishedangel said:**
> 
However there is a program out there that does enable windows to read ext file systems you just gotta Google it and you will eventually find it.

Yes one is ext2read which is a free programme...but there are several.

@haqking... no more coffee for you...):P

---

### Post by Wiking on 2011-09-11
> **Enigmapond said:**
> Yes one is ext2read which is a free programme...but there are several.

@haqking... no more coffee for you...):P

I downloaded ext2read and ran it as an admin but when it scans nothing happens, it just stays blank.. Any ideas?

This is what the log displays: 

```
Error Opening \\.\PhysicalDrive3. Error Code 2
No of disks 3
Scanning \\.\PhysicalDrive0
index 0 ID 7 size 703277442 
Scanning \\.\PhysicalDrive1
index 0 ID 7 size 683726337 
Scanning \\.\PhysicalDrive2
index 0 ID 82 size 1250258944 
Error Opening \\.\PhysicalDrive3. Error Code 2
No of disks 3
Scanning \\.\PhysicalDrive0
index 0 ID 7 size 703277442 
Scanning \\.\PhysicalDrive1
index 0 ID 7 size 683726337 
Scanning \\.\PhysicalDrive2
index 0 ID 82 size 1250258944 
Error Opening \\.\PhysicalDrive3. Error Code 2
No of disks 3
Scanning \\.\PhysicalDrive0
index 0 ID 7 size 703277442 
Scanning \\.\PhysicalDrive1
index 0 ID 7 size 683726337 
Scanning \\.\PhysicalDrive2
index 0 ID 82 size 1250258944 
Error Opening \\.\PhysicalDrive3. Error Code 2
No of disks 3
Scanning \\.\PhysicalDrive0
index 0 ID 7 size 703277442 
Scanning \\.\PhysicalDrive1
index 0 ID 7 size 683726337 
Scanning \\.\PhysicalDrive2
index 0 ID 82 size 1250258944 
```

---

### Post by catlover2 on 2011-09-11
[Ext2Fsd](http://www.ext2fsd.com/) has worked flawlessly for me on XP 32 bit and Win7 64 bit, and it has a pretty user-friendly GUI for assigning drive letters.

---

### Post by mrcoolinux on 2011-09-11
Hi, i use this for windows 7 to see ext 2,3 and4 files on my hd.
[http://www.fs-driver.org/download.html](http://www.fs-driver.org/download.html)
hope that helps!

---

### Post by sffvba[e0rt on 2011-09-11
Could I just add a voice of caution here when trying to access data on partitions that are not nativity supported by the operating system you are using... make sure you have backups so if something goes wrong you don't loose priceless and irreplaceable files.


404

---

### Post by Wiking on 2011-09-11
I downloaded ext2Fsd.

I closed it, ran it again, and was able to assign a letter to it using the second option. Am I suppose to see it in Windows Explorer? Because it does not show up. 

Another interesting thing the program shows is that for that particular drive E it says;

File system: NTFS
Partition type: Linux swap

So I assume drive E, that Windows can't read, is still NTFS but corrupted (I formatted wrong). So I assume all these ext2 reader programs will not work for drive E?

Luckily I can still see the files when I use Kubuntu, and can move them to a blank NTFS formatted drive.

---

