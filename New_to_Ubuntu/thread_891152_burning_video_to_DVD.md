---
title: "burning video to DVD"
date: 2008-08-15
forum: New to Ubuntu
---

### Post by jethier on 2008-08-15
Hi:
a quick question about burning a video to DVD. I have a video and its in a strange format I'm not familiar with.

It's in two folder called CD1 and CD2. within CD1 theres numerous files (box looking icons) and the names are aaf-movietitle.cd1.r00 all the way to aaf-movietitle.cd1.r47 and then theres one named aaf-movietitle.cd1.rar
Exactly the Same for CD2.

How do I burn this onto a DVD so I can lend it to my friend?

I tried Basero but the four options available (Audio project, Data project, Disc copy and Burn image) don't seem to apply to my situation.

Any help for this Newb is greatly appreciated.

---

### Post by nicedude on 2008-08-15
The files you list are RAR chunks , as in compressed files that have been zipped into say 15MB chunks ( 15MB common with pirates :-) ) first you need to unzip the files and get the video out, it will then be AVI or MPEG etc . At that time you could use a DVD authoring program to convert these files to DVD standard and burn them to a disk. Sorry I can't tell you what to use to do this in Linux as I still use windows if I want to author a dvd since I have professional level tools that are not available in linux ( cinema craft encoder :-) ) and as such I don't use linux for DVD authoring. There are conversion and authoring programs available though and I am sure someone can sound off as to what they are. So copy the contents of the disks to a directory on your desktop and Unrar them, then follow the advice that I am sure someone can provide as to a DVD authoring program in Linux.

Someone post what program does AVI to MPEG2 conversion & authoring for this person please.

---

### Post by niyonk on 2008-08-15
hi, :)
You need to be able to open rar files first

go to System->Admninistration->software sources and enable the Multiverse Repository
then,
run 'sudo apt-get install unrar' in terminal to install rar capabilities ;)

open aaf-movietitle.cd1.rar and choose extract to any folder of your choice, that should be the movie :)



And also try K3B for burning 
Cheers!

---

### Post by tahina on 2008-08-15
Before you can unpack the rar-archives you need to install unrar. Open a terminal and...
```
sudo apt-get install unrar
```

It's in the multiverse repository, which has to be enabled first. You can enable it from "Software Sources" in the Sytem>Administration menu.

Then you should be able to unpack by right-clicking the first file (.r01 or .rar probably) and choosing "Extract here".

:) I'm too slow...

---

### Post by niyonk on 2008-08-15
> **tahina said:**
> Before you can unpack ...

:) I'm too slow...

lol, you are not the only one :biggrin:

---

### Post by nicedude on 2008-08-15
K3B isn't going to convert this persons AVI to a valid MPEG2 stream and burn it with menus etc to a DVD so could someone please tell this person what program in linux will allow them to do that. I am sure someone here converts avi's to DVD and authors them in linux, I don't but I like professional tools for this and linux doesn't have any so I don't know this part of the equation. And good looking out on the installing RAR support I forgot that it isn't there by default.

---

### Post by niyonk on 2008-08-15
[http://ubuntuforums.org/showthread.php?t=733686](http://ubuntuforums.org/showthread.php?t=733686) seems to suggest DeVeDe :)

or try the other options given in that thread

---

### Post by jethier on 2008-08-15
Wow, thanks a lot guys (or possibly gals)I really appreciate the clear and concise instructions!

I now have two .avi files in a folder. 

I want to get these two .avi files into MPEG2 format with seamless transition. Apparently K3B can't do this.

Anybody know of a program that can do this?

---

### Post by jethier on 2008-08-15
> **niyonk said:**
> [http://ubuntuforums.org/showthread.php?t=733686](http://ubuntuforums.org/showthread.php?t=733686) seems to suggest DeVeDe :)

or try the other options given in that thread

Oh thanks, I didn't see that.

---

### Post by nicedude on 2008-08-15
Since no one else will sound off I searched to find out what you could look at installing to do this. These are all in the repositories


videotrans - DVD video conversion utils

dvdauthor - create DVD-Video file system from a valid MPEG2 stream

devede - program to create video DVDs - try this one first as I think it might be easiest/best


I have no experience with these though

---

### Post by jethier on 2008-08-15
> **nicedude said:**
> Since no one else will sound off I searched to find out what you could look at installing to do this. These are all in the repositories


videotrans - DVD video conversion utils

dvdauthor - create DVD-Video file system from a valid MPEG2 stream

devede - program to create video DVDs - try this one first as I think it might be easiest/best


I have no experience with these though

Thanks a lot! I will try devede.

---

