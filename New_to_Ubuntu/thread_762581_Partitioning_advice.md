---
title: "Partitioning advice"
date: 2008-04-22
forum: New to Ubuntu
---

### Post by 3dgimp on 2008-04-22
I want to dual boot Windows & ubuntu. I have 440GB HDD space in total (with stuff filling most of it...but I'll worry about that).

I run Steam with CS:S & Trackmania. So that's really all I NEED for Windows. How does this sound for partitioning:

Disk 1 : 120GB
30GB - Windows (NTFS)
90GB - MP3s (NTFS)

Disk 2 : 320GB
30GB - ubuntu (EXT3)
8GB - Swap (SWAP) (I have 4GB RAM....2*RAM is the general rule for swap?)
282GB - Films/Downloads etc (NTFS)

I want the music and downloads HDDs available to both OS's. I also remember from somewhere that it's better to have the two OS's on different physical drives as well. Is there any truth to that? Does this setup seem adequate? Would I be able to install both linux & windows applications on the NTFS drives?

Ta

---

### Post by LazarUbus on 2008-04-22
Your configuration seems to be fine.

> **3dgimp said:**
> Would I be able to install both linux & windows applications on the NTFS drives?
What exactly do you mean???
Linux applications will be installed in ext3, windows applications on ntfs.

---

### Post by philinux on 2008-04-22
With 4g ram You dont need that much swap, 2gigs would be enough.

---

### Post by aeiah on 2008-04-22
that setup seems fine. if your hard drives not on the same IDE cable, you may get a bit more performance by having your swap partition on the windows drive (and your windows pagefile on the ntfs partition on the linux drive).

and yea, i find it simpler to have windows on one and linux on the other. it makes things easier if you have to reinstall windows or if one of the drives fails.

incidentally, steam and CS have decent support under wine in linux i believe, although i wouldnt do anything too rash as people still have problems.

---

### Post by Jimmy9pints on 2008-04-22
If you want the music and downloads HDDs available to both OS's then you can just keep it on the NTFS and mount in Ubuntu. This can be done automatically by following the advice in this post:

[http://ubuntuforums.org/showthread.php?t=761373](http://ubuntuforums.org/showthread.php?t=761373)




Hope that helps

---

### Post by woaiwojia on 2008-04-22
> **philinux said:**
> With 4g ram You dont need that much swap, 2gigs would be enough.

i think 1gigs is enough,maybe 2gigs would be better.

---

### Post by prshah on 2008-04-22
> **3dgimp said:**
> 
Disk 1 : 120GB
30GB - Windows (NTFS)
90GB - MP3s (NTFS)
Disk 2 : 320GB
30GB - ubuntu (EXT3)
8GB - Swap (SWAP) (I have 4GB RAM....2*RAM is the general rule for swap?)
282GB - Films/Downloads etc (NTFS)


A better scheme would be to put your ubuntu on the first drive and "/home" on the second: eg:

Disk 1 : 120GB
30GB - Windows (NTFS)
10Gb - ubuntu (ext3), mount point "/"
4.4GB - Swap (SWAP)
Balance - MP3s/whatever (NTFS)
Disk 2 : 320GB
30GB - (or how much ever) ubuntu (EXT3), mount point "/home"
Everything else - Films/Downloads etc (NTFS)[/quote]

This way, your "/" and "/home" can be accessed simultaneously and will add that little bit extra speed/smoothness.

> **philinux said:**
> With 4g ram You dont need that much swap, 2gigs would be enough.

You need atleast as much swap as RAM if you plan on using hibernation, since the swap area is used to write the hibernation information. Since you have so much RAM, you swap will hardly ever be used except for hibernation. Also, an additional 5%/10% as a safety margin in case of bad sectors.

---

### Post by 3dgimp on 2008-04-22
Cheers for the advice guys. I'm going to look into all this over the following week or so. Just wanted to get started on moving stuff around to free up space.

@LazarUbus: I was being an idiot for a second there. What I meant was I wanted access to them...nothing to do with apps (as these are installed in the differing OSs partitions...durrr), and as people have said I can mount these. Thanks.


Ta to everyone for the help. Hey, maybe because of you lot there'll be another full time ubuntu user in the world. :-D

---

