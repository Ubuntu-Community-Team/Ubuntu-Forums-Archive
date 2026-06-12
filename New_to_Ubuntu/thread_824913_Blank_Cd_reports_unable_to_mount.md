---
title: "Blank Cd reports unable to mount"
date: 2008-06-10
forum: New to Ubuntu
---

### Post by Midgetprawn on 2008-06-10
Heya
Same old story but.. I can sometimes mount a blank disc to burn data after much opening and closing of my dvd rom and trying random buttons but usually it says cannot mount or no media found.

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=39c5f886-057d-4e3c-a784-0769553cb439 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=3399d1d8-0579-46bf-b66a-8227db5f722c none            swap    sw              0       0
/dev/scd0       /media/cdrom0   auto,user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0


Also having problems with UDF volume discs which have been burned on Windows

Currently on Hardy kernel 2.6.24-19-generic

---

### Post by Midgetprawn on 2008-06-10
Can't find help in backlog of files too

---

### Post by Midgetprawn on 2008-06-10
Ok so I have dowmloaded Gnomebaker which has burned one copy but now persists in failing on others. The computer fials to recognise that blank discs are in the burner and Brasero says  No disk
Currently using Imation 700 CD-R discs

---

