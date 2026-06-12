---
title: "[SOLVED] umask, dmask, and fmask - What do the values mean?"
date: 2008-07-27
forum: New to Ubuntu
---

### Post by koji042 on 2008-07-27
I've been learning how to use fstab in Ubuntu and I was wondering what the values for umask, dmask, and fmask mean . I know they have something to do with permissions for FAT32, but I couldn't find anything specifically explaining the syntax. Such as what umask=000 or fmask=027 means. I've tried looking through the [Ubuntu documentation page on fstab]("https://help.ubuntu.com/community/Fstab") and the [Linux Man Pages]("http://linux.die.net/man/8/mount") to no avail.

Also, does each *mask deal with a different part of the FAT32 filesystem? Like one for files, folders, etc. And if so, which is which?

I've been stuck on this for a while, so any help is greatly appreciated. Thank you very much. :)

---

### Post by scragar on 2008-07-27
same numbering system as chmod offers [http://en.wikipedia.org/wiki/File_system_permissions#Octal_notation](http://en.wikipedia.org/wiki/File_system_permissions#Octal_notation)

---

