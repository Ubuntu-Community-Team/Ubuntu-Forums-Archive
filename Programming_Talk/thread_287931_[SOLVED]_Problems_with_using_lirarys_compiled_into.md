---
title: "[SOLVED] Problems with using lirarys compiled into /usr/local"
date: 2006-10-29
forum: Programming Talk
---

### Post by Keith Hedger on 2006-10-29
I've got a bit of a problem that has cropped up a couple of times I hope someone can help!

I've recently complied and built gtkpod and libgpod from source (the one in the repo wont do), during compiling the gtkpod make seems to find the right library version (in /usr/local/lib) but when i run it it tries to use the one installed in the usual lib folder, how can I get an app to look in /usr/local/lib either by default of after trying /lib, if I remove the one in /lib I simply get an error saying:

"gtkpod: error while loading shared libraries: libgpod.so.0: cannot open shared object file: No such file or directory"

This is a problem I've had with other programs so a 'PROPER' solution would be nice.

Althogh I'm a resonably experianced programmer I'm fairly new to Linux and I seriously want dump OS X!

Thanks in advance!

---

### Post by po0f on 2006-10-29
Keith Hedger,

According to [this](http://www.eyrie.org/~eagle/notes/rpath.html), you should double-check /etc/ld.so.conf to make sure that /usr/local/lib is in the library search path (no reason it shouldn't be), and probably more importantly, make sure you run `ldconfig` after adding libraries to your system.

---

### Post by hod139 on 2006-10-29
Just to add to the previous post, the file may not exist on your machine.  If it doesn't, just create the file, and add 
```
/usr/local/lib

```as the only line.

**Edit:** As a second thought, all of this must be done with superuser rights. (even running ldconfig)

---

### Post by Keith Hedger on 2006-10-30
Thanks guys mostly it worked after i created the ld config file, still had a similar problem with another program and had to resort to removing the old library in /lib, but that was probably cos of the development files installed with the lib.

thanks again:D

---

