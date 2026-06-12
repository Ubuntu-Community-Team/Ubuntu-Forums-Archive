---
title: "trouble compiling vlc (0.9.8a, git)"
date: 2008-12-14
forum: Packaging and Compiling Programs
---

### Post by Meow27 on 2008-12-14
```
(cd .libs && rm -f libvlc.so.2 && ln -s libvlc.so.2.0.2 libvlc.so.2)
(cd .libs && rm -f libvlc.so && ln -s libvlc.so.2.0.2 libvlc.so)
creating libvlc.la
/bin/sed: can't read Files/vlc-1.0.0-git/src/libvlccore.la: No such file or directory
libtool: link: `Files/vlc-1.0.0-git/src/libvlccore.la' is not a valid libtool archive
make[4]: *** [libvlc.la] Error 1
make[4]: Leaving directory `/home/username/Program Files/vlc-1.0.0-git/src'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/username/Program Files/vlc-1.0.0-git/src'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/username/Program Files/vlc-1.0.0-git/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/username/Program Files/vlc-1.0.0-git'
make: *** [all] Error 2
username@Nebula-Class:~/Program Files/vlc-1.0.0-git$ 


```

i think i configured it fine, it didnt say i was missing any dependencies (after a long time of searching for them >_<)

anyhow, ive been seeing this same exact error (whatever it would be called in this case) for a while, and i have no idea what it means......is there anyway to get through this (no i cant use git packages cause im using hardy)


thanks in advance

---

### Post by Meow27 on 2008-12-16
well i was able to spot the problem, one of the folders i was using had a space (program files) so all waht i needed to do was to rename it Program_files and it worked....at least i got thru that problem...


i encountered another error, but for the lack of an audience i wont post in this board....

---

