---
title: "Ability to fully format NTFS?"
date: 2008-09-09
forum: New to Ubuntu
---

### Post by skymera on 2008-09-09
Hello

My XP install has gone mad and reserved 20% of my gaming drive for MFT!? Which is a lot of space i can't use and it's all on the outer tracks.

The only way for me to get rid is to fully format my drive.

I want to use Ubuntu to copy the WHOLE drive contents to my other, format as NTFS (full format)and copy my drives contents back.

But will this affect Windows from Ubuntu?

The drive is D: and i want to copy to C: and format then copy back over. Will it still be called D:?

Is doing it in Windows with 3rd party apps better?

---

### Post by BDNiner on 2008-09-09
if you make sure not to format your C drive you should be fine. You can rename the drive letters from inside windows. so it does not matter what drive letter ubuntu gives the partition after it is formatted.

IMO it might be easier to do this within windows. just copy everything to C: and then go into disk management and format the drive and copy everything back.

---

### Post by mc4man on 2008-09-09
I'd probably do it from windows
> The only way for me to get rid is to fully format my drive.
Back when I was using windows I purchased a prog for removing unused entries in the mft, thereby reducing or maintaining size (I don't remember which
There is a 25-run trial, don't know if it will help but anyway or for future use to keep it clean (i used to run at least once a week or after major deletions

[http://www.briggsoft.com/dsnoop.htm](http://www.briggsoft.com/dsnoop.htm)

---

### Post by SkonesMickLoud on 2008-09-09
> **BDNiner said:**
> so it does not matter what drive letter ubuntu gives the partition after it is formatted.

Ubuntu will not assign the partition any drive letter, as that is a Windoze thing.

As for copying your entire Windoze install check out Partimage:

[http://www.partimage.org/Main_Page](http://www.partimage.org/Main_Page)
[http://www.partimage.org/Partimage-manual_Usage](http://www.partimage.org/Partimage-manual_Usage)

---

### Post by yaztromo on 2008-09-09
You can use dd in linux to copy the drive.

---

### Post by BDNiner on 2008-09-09
> **SkonesMickLoud said:**
> Ubuntu will not assign the partition any drive letter, as that is a Windoze thing.

As for copying your entire Windoze install check out Partimage:

[http://www.partimage.org/Main_Page](http://www.partimage.org/Main_Page)
[http://www.partimage.org/Partimage-manual_Usage](http://www.partimage.org/Partimage-manual_Usage)

yes this is correct, windows will assign the drive letter when you book back to XP.

---

### Post by skymera on 2008-09-09
Awesome.

I tried copying all my D contents to C: but i got an error saying "Low system Resources" i had like 40GB left, so i'm not sure what.

"checking out links"

---

### Post by SkonesMickLoud on 2008-09-09
> **skymera said:**
> Awesome.

I tried copying all my D contents to C: but i got an error saying "Low system Resources" i had like 40GB left, so i'm not sure what.

"checking out links"

Any more you could post on that error?  What program are you using?

---

### Post by skymera on 2008-09-09
I was just using copy and paste in Windows XP.

I would show you again but it means copying about 65GB worth of stuff over.
I'm thinking it was just temporary space as i have 2.6GB RAM left, and plenty of disk space. Doesn't make sense.

I'm in XP now trying to find a way to copy everything over, or at least make a backup.
I tried to make an ISO of the drive, which just errored too.

---

### Post by skymera on 2008-09-09
Sorry just had a look and calculated. About 17GB of my drive is reserved for the damn MFT.

Places i've read  say it should be around 50MB. 

This thread seems to have changed a bit. Sorry.

---

### Post by SkonesMickLoud on 2008-09-09
> **skymera said:**
> Sorry just had a look and calculated. About 17GB of my drive is reserved for the damn MFT.

Places i've read  say it should be around 50MB. 

This thread seems to have changed a bit. Sorry.

IIRC the maximum that an MFT can be is 4096 bytes...

---

### Post by skymera on 2008-09-09
17GB reserved. *reserved* not in use, 

screeny:
[[IMG]http://img74.imageshack.us/img74/2007/mftreserveduu9.th.jpg[/IMG]](http://img74.imageshack.us/my.php?image=mftreserveduu9.jpg)

---

### Post by skymera on 2008-09-10
Anyone know of a good backup software?

Basically just to copy EVERYTHING from D: to C: as a .rar or .iso or whatever, so i can extract again.

---

