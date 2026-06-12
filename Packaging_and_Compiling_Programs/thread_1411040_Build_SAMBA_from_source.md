---
title: "Build SAMBA from source"
date: 2010-02-19
forum: Packaging and Compiling Programs
---

### Post by bengtner on 2010-02-19
I'm trying to build a new SAMBA version for test purposes. I've managed to build SAMBA from source with make  and tried to upgrade by running 

make install

However, it seems like the binaries end up in a different place than Ubuntu would like to find them.

Restarting the SAMBA services will just restart the original 3.4 version, not 3.5.0rc2 that I just build. 

I must admit I don't have that much experience of Linux, so probably I've tried to do something real stupid. Any help on this is appreciated.

---

### Post by doas777 on 2010-02-19
well you need to link to the new version as close as i can tell. I don;t have samba installed here, but I would start by running 
```
which samba
```then once i found where the link is (perhaps /usr/bin/...) I would run 'ls -l' on that directory to see if samba is a link, and to where it is pointing. once you have found it, make sure it is correct, and if not, point the link to the desired version. this [howto]("http://wiki.samba.org/index.php/Samba4/HOWTO") , says that it installs into /usr/local/bin by default, so you want to point your link there.

---

