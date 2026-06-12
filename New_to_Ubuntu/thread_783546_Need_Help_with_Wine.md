---
title: "Need Help with Wine"
date: 2008-05-05
forum: New to Ubuntu
---

### Post by BlackSwordD2 on 2008-05-05
ok i installed it and followed all the instructions on the site WineHQ

even watched a tutorial on how to use it on YouTube ([http://www.youtube.com/watch?v=Q564OEmseXE&feature=related](http://www.youtube.com/watch?v=Q564OEmseXE&feature=related))

but i seem to have an error, i have very similar conditions as in the video where i have XP installed first and now Ubuntu so i have old programs still installed there. however, Wine cant seem to detect any of them except Notepad. i even followed the exact steps he used to open Winamp (which i conveniently already have on my XP) but it can't find the file

so i need an idiots guide to fix this if possible

Please and Thank you!

---

### Post by Xiong Chiamiov on 2008-05-05
Windows is installed on a different partition than Linux.  Wine uses a directory on your linux partition to fake a windows install.  I personally don't have Windows installed at the moment (pending reinstall after some repartitioning), but wine works just great.

If you want to install, say, winamp (though I wouldn't - use amarok or something), then download the .exe and open it with wine.

---

### Post by BlackSwordD2 on 2008-05-05
> **Xiong Chiamiov said:**
> Windows is installed on a different partition than Linux.  Wine uses a directory on your linux partition to fake a windows install.  I personally don't have Windows installed at the moment (pending reinstall after some repartitioning), but wine works just great.

If you want to install, say, winamp (though I wouldn't - use amarok or something), then download the .exe and open it with wine.

yea i have no problem installing new things (as long as they are supported apps)

but i saw with my own eyes and heard with my own ears in that tutorial that i could use previously installed apps on the other OS

---

### Post by shae on 2008-05-05
Please post the results of the following command so I can further help you:

```
cat /etc/fstab
```

---

### Post by aktiwers on 2008-05-05
The problem is that Windows has the registry. So the app already installed on Windows has it's registry keys on your windows install and not in Wine.

If you are trying to install winamp (why would you do that?) you could try Wine-doors.
It downloads and installs it automatically for you.
[http://www.wine-doors.org/wordpress/](http://www.wine-doors.org/wordpress/)

Just download the .deb file and double-click it.

But you should try xmms, xmms2 or** Audacios** which are all very simular to winamp and you can even install winamp themes on them.

---

### Post by BlackSwordD2 on 2008-05-05
> **shae said:**
> Please post the results of the following command so I can further help you:

```
cat /etc/fstab
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2
UUID=05472d09-51b7-481c-98a5-fb7993108516 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=065acef9-0287-4c84-a969-94c358c20766 none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by ant2ne on 2008-05-05
> **BlackSwordD2 said:**
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2
UUID=05472d09-51b7-481c-98a5-fb7993108516 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=065acef9-0287-4c84-a969-94c358c20766 none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

You got no mounted NTFS or FAT. So you can't even read much less write to your windows partitions. I assume it is hda1.

The other posters do have a point that you should be more familiar with the ubuntu equivalents of apps. 

But if your goal is to learn wine, first learn that wine is buggy, and you eliminate many bugs by installing the apps into your ~/.wine by using the wine command line. I love wine, and fight with it daily.

---

### Post by BlackSwordD2 on 2008-05-05
> **ant2ne said:**
> You got no mounted NTFS or FAT. So you can't even read much less write to your windows partitions. I assume it is hda1.

The other posters do have a point that you should be more familiar with the ubuntu equivalents of apps. 

But if your goal is to learn wine, first learn that wine is buggy, and you eliminate many bugs by installing the apps into your ~/.wine by using the wine command line. I love wine, and fight with it daily.

awesome....

so... 

how do i mount it?

P.S. i understand fully for the Ubuntu Equivalents and i love them all i was using winamp as more or less an example. i plan to use Wine more for my games that i have already installed as opposed to haveing it installed twice on the same comp... also to use Word to type school papers in case i need to switch back and forth

---

