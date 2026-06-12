---
title: "Places.. shortcuts?"
date: 2008-08-14
forum: New to Ubuntu
---

### Post by NightKry97 on 2008-08-14
I have Ubuntu with Vista dualboot...
 
Is there a way to make things such as Places>Documents, open up the Vista Documents?

Thanks

---

### Post by Separ on 2008-08-14
Navigate to the folder using Nautilus and go Bookmarks > Add Bookmark.

Alternatively you could make the Documents folder a symlink to the Vista Documents folder if you just want everything to go there.

---

### Post by NightKry97 on 2008-08-14
Thank you =D

---

### Post by bodhi.zazen on 2008-08-14
Not directly ...

You first need to mount your windows partition.

Then you could make a link to your documents in your home directory.

_Windows:_ [Psychocats Mount windows ](http://www.psychocats.net/ubuntu/mountwindows)
For read-write: 
[list=number]
[*]vfat (FAT) use dmask=027,fmask=137
[indent]more permissive permissions : dmask=000,fmask=111[/indent]
[*]ntfs use [ntfs-3g](http://ubuntuforums.org/showthread.php?t=217009) and a fstab entry something like this:
```
/dev/hda1  /media/windows  ntfs-3g  defaults  0  0
```
[*]An alternate is ntfs-config. ntfs-config uses ntfs-3g to mount windows partitions via a gui :)
[indent][http://ubuntuforums.org/showthread.php?t=337970](http://ubuntuforums.org/showthread.php?t=337970)[/indent]
[/list]


Then you just :

sudo ln -s /media/windows/path_to_My \ Documents ~/My\ Documents

Take care, Linux does ot like spaces in directory of file names. You need to quote them

"My Documents"

Or "escape" them with a \

My\ Documents

---

