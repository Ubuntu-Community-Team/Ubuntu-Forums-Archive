---
title: "NTFS defrag from Ubuntu/Ubuntu Console"
date: 2008-06-20
forum: New to Ubuntu
---

### Post by SonicComKid on 2008-06-20
Okay, before I start, I already searched around forums and everyone keeps saying the same thing about ditching NTFS and installing ext3, even if windows is installed on that drive and using the driver hack on windows to make it use ext3 (which I'll post below for anyone who searches this)

I'm looking for a way to defrag my NTFS partitions/drives from Ubuntu either from the Gnome desktop or even better if possible form the console. Does anyone know any tools that can do that?

My reason is this: 
1. Defrag works a heck of a lot better if the OS on it isn't trying to use files while you defrag. 
2. Defragging with an external OS works a lot faster 
3. Face it, window's defrag sucks and Ubuntu is a million times more efficient and stable and finally 
4. Defraging from Ubuntu will also ignore those pesky 'read-only' and 'system' flaged files and actually defrag them, unlike what windows would.

Can someone please tell me of anything that'd defrag my NTFS drives nicely?

------------------------------
> ext on windows post:

Why is it NTFS? If its so you can use it with other computers and can't install ext2/3 driver on them, then can you not use that machine to defrag it?

If there is no reason to have NTFS, ditch it, copy the data to another disk, and re-format using ext3.
Leave a 15MB partiton as VFAT to hold the windows ext2/ext3 driver on it, so you can install on any machine to view your data.

[http://www.ext2fsd.com/](http://www.ext2fsd.com/)

Or maybe better:

[http://www.fs-driver.org/index.html](http://www.fs-driver.org/index.html)

---------------------------

---

### Post by bodhi.zazen on 2008-06-20
I am not aware of a ntfs defrag tool you would run on Linux.

If you run windows defragement it with windows. If you do not like the windows tools, perhaps you should take the subject up with Microsoft. :lolflag:

If you run linux full time fragmentation is but one of many reasons to convert to a linux native file system (ext3).

[http://www.linux-ntfs.org/doku.php?id=ntfsdefrag](http://www.linux-ntfs.org/doku.php?id=ntfsdefrag)

---

### Post by dark_harmonics on 2008-06-20
I am also not aware of a tool but had an idea. Why not boot to a WINPE2.0 or bartpe boot cd/usb drive. That way you could perform this maintenance on your windows partitions using windows tools. It actually makes sense.

After all we wouldn't want the reverse: trusting any windows tools to mess with my linux!

check out the vista WAIK. You download the IMG file, Burn it to CD or mount it to a virtual CD drive. Install the WAIK and it will put some help files there. Inside those help files are exact procedures for building a WINPE USB or CD media. Alternatively you can just download an ISO from Bart PE that will allow you to do the same sort of things.

---

### Post by hyper_ch on 2008-06-20
> **bodhi.zazen said:**
> [http://www.linux-ntfs.org/doku.php?id=ntfsdefrag](http://www.linux-ntfs.org/doku.php?id=ntfsdefrag)

lol

> 
About ntfsdefrag

ntfsdefrag does not yet exist. 


---

### Post by ukripper on 2008-06-20
Why don't you backup all your NTFS data and then reformat the drive in ext3? if you are not using windows then no point having NTFS in first place or am i missing something?

---

### Post by SonicComKid on 2008-06-20
To reply to all of you,

Firstly I'm triple-booting this computer XP/Vista/Ubuntu, most of my drives are NTFS because of my video games that only work on XP or Vista depending on the game (Wine failed me.. can't run almost any of my games it seems). Trying to find a place to shunt over 500GB then shunt back is a very very inconvent way of defragging.

I also do not want to teach windows a new trick and hack it to use ext3. I had enough headakes getting XP, Vista, and Ubuntu to get along with eachother and not screw around with eachother's boot sectors.

I actuall do have a windows XP BartPE disc which has come in handy every so often, but from what I could tell the disc defragger that's avaiable on it sucks worse than window's own built-in one. The defragger it comes with is made by some theird party that's using a defragger that looks like it was striped from a windows 98 machine.

I would have thought someone would have made an NTFS defragger for Linux by now since they already made what seems to be a perfect open-sourced NTFS file system reader/writer that Ubuntu has built-in now.

---

