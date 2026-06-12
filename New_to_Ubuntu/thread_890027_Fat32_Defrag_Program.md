---
title: "Fat32 Defrag Program"
date: 2008-08-14
forum: New to Ubuntu
---

### Post by Tom--d on 2008-08-14
hello,

Are there any Defrag programs for FAT32. Its for my external Hard drive.
Would prefer if it was in the repositories. 


Thanks,
Tom

---

### Post by Pro-reason on 2008-08-15
You could try *shake*.  I think it works for any filesystem.

You could also just defrag while you are on Windows.

Or reformat the drive as ext3 if you don't use Windows.

---

### Post by nicedude on 2008-08-15
I looked around on the web and couldn't find anything that defrags FAT32 while in linux so I think your best bet would be to either use a windows box to defrag it or to copy the data to somewhere else and make the portable a ETX3 or NTFS partition and then copy it back. If you know where you can lay your hands on a copy of partition magic ( a commercial partition program that boots on cd ) then it can convert your FAT32 to NTFS while there is data on it, but even then I wouldn't bet my life on no data loss ( so backing up somewhere else would still be a good idea )

hope this helps

---

### Post by Pro-reason on 2008-08-15
Why would you convert to NTFS?

---

### Post by rockerphil on 2008-08-15
> **Pro-reason said:**
> 
Or reformat the drive as ext3 if you don't use Windows.

agreed, i'd personally back up what data is on the external and then reformat it to an ext3 partition, Linux plays a lot nicer with it than a FAT system, and ext2/ext3 doesn't fragment

---

### Post by Paqman on 2008-08-15
> **Pro-reason said:**
> Why would you convert to NTFS?

Why wouldn't you? It's a much more modern, efficient file system than FAT32, while still retaining compatibility with Win boxes. The only reason to use FAT32 is if you need Linux/Mac/Win compatibility.

---

### Post by Sef on 2008-08-15
> agreed, i'd personally back up what data is on the external and then reformat it to an ext3 partition, Linux plays a lot nicer with it than a FAT system, and ext2/ext3 doesn't fragment

It can defragment, but it is usually not a problem unless your hard disk is more than 90% full.

---

### Post by Pro-reason on 2008-08-15
> **Paqman said:**
> Why wouldn't you? It's a much more modern, efficient file system than FAT32, while still retaining compatibility with Win boxes. The only reason to use FAT32 is if you need Linux/Mac/Win compatibility.

I was thinking that if he was going to be regularly connecting it to Windows, then there'd be no reason to change anything (he could defrag there), and if he was not really going to be using it with Windows, he could give it a native Linux format, making defragging largely unnecessary.  With NTFS, he'd have the hassle of reformating, he'd still have to defrag it, there would still not be good defrag utilities for it on Linux, and there would be occasional glitches using it with Linux (see this forum for NTFS mount problems).  Plus NTFS is evil.

---

### Post by Tom--d on 2008-08-17
The reason I have it on Fat32 is I have a xbox360 and would like to play things off the hard drive.

Should I have NTFS or keep it as Fat32?

---

### Post by lisati on 2008-08-17
> **Paqman said:**
> Why wouldn't you? It's a much more modern, efficient file system than FAT32, while still retaining compatibility with Win boxes. The only reason to use FAT32 is if you need Linux/Mac/Win compatibility.
I don't know if Win98 can cope with NTFS without help....

---

### Post by Pro-reason on 2008-08-17
> **Tom--d said:**
> The reason I have it on Fat32 is I have a xbox360 and would like to play things off the hard drive.

Should I have NTFS or keep it as Fat32?
If it's mainly for the XBox, FAT is probably the best filesystem.  The Xbox internal harddrive uses FATX, which is a slight variation on FAT.  I've just done a bit of fast Google-research, and it seems that the XBox is not capable of reading NTFS drives.  That's incredibly stupid, because Microsoft is trying to phase FAT (in favour of NTFS) out on the PC, and yet they have made it necessary on their gaming console.

I believe that Con Kolivas' *shake* utility can defrag any drive, because it works by just moving files around rather than doing deep filesystem stuff.  Try that.  Also, don't worry about fragmentation so much.  I'm sure the Xbox will read your fragmented media just fine.

---

### Post by jjaflague on 2010-11-20
> **Tom--d said:**
> The reason I have it on Fat32 is I have a xbox360 and would like to play things off the hard drive.

Should I have NTFS or keep it as Fat32?


I've got the same problem here...as far as I can tell, all these video gaming console designers programmed their OS's to only recognise external media in FAT32 format.  If you're using your external hard drive for movies/music/pictures on your Xbox, DO NOT reformat to NTFS--it won't work any longer.  I'm searching for a formatting utility that will reformat large externals, (1TB or better), back to FAT32.  Most techies out there think this is ludicrous because NTFS is the "way ahead" as far as making the most out of your digital space with these larger externals, but as I've found out through many trial and errors, (and a few shot externals now...*&$$&%#$dammitt...), none of these most recent video game consoles will read an NTFS-formatted external...

GLIMMER OF HOPE: The free download "Swissknife" will reformat large external drives, or any drive connected to your computer for that matter.  However, it only seems to work the best on Windows XP.  It's notorious for crashing on Vista and 7, and as far as I can tell, I can't even get it to install properly here on Ubuntu.  I'm new to this OS and I'm very interested in what I've experienced so far, so if there's ANYONE out there who may know a trick or two that I should try, please let me know.

On another curious note--if there's anyone who has any idea why Sony and Microsoft programmed their gaming consoles to only work with FAT32, I know I'd appreciate more knowledge on this matter as it may help clear up any future misunderstandings.

---

### Post by mike555 on 2010-11-20
You might be able to run a portable version of defrag in wine, but I haven't tried it ......

---

### Post by Pro-reason on 2010-11-20
> **jjaflague said:**
> I'm searching for a formatting utility that will reformat large externals, (1TB or better), back to FAT32. 

I’m not aware of any particular problem with formatting larger drives, as long as they are under the 2TB limitation of FAT32.  Do you mean to say you have used Ubuntu’s standard formatting utility (GParted) and it didn’t work?

---

