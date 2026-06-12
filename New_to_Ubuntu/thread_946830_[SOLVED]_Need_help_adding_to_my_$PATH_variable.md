---
title: "[SOLVED] Need help adding to my $PATH variable"
date: 2008-10-13
forum: New to Ubuntu
---

### Post by DFord425 on 2008-10-13
what command do i use to add another directory to my $PATH. Is it PATH:=*new_directory*?

---

### Post by unutbu on 2008-10-13
```
PATH=$PATH:new_directory
```
See [http://ubuntuforums.org/showpost.php?p=5953944&postcount=2](http://ubuntuforums.org/showpost.php?p=5953944&postcount=2)

---

### Post by MusicMastaMike on 2008-10-13
PATH=$PATH:/data/myscripts
export PATH

[http://www.troubleshooters.com/linux/prepostpath.htm](http://www.troubleshooters.com/linux/prepostpath.htm)

---

### Post by spiderbatdad on 2008-10-13
[http://ubuntuforums.org/showthread.php?p=5123037](http://ubuntuforums.org/showthread.php?p=5123037)

lol lot of links popped up fast...set it in .bashrc:```
export PATH=$PATH:$HOME/geda-install/bin
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:$Home/geda-install/lib
```an example from the link above, so that you dont have to add the path every session.

---

### Post by DFord425 on 2008-10-13
Thank you all.

---

