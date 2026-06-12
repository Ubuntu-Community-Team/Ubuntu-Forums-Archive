---
title: "error in the make install process"
date: 2008-10-18
forum: New to Ubuntu
---

### Post by jimmerlin on 2008-10-18
when i was installing sdl&#65292;configure ok &#65292;checkinstall:

/usr/bin/install -c build/.libs/libSDL.a /usr/local/lib/libSDL.a
chmod 644 /usr/local/lib/libSDL.a
chmod: changing permissions of `/usr/local/lib/libSDL.a': No such file or directory
make: *** [install-lib] Error 1

if libsdl.a installed 
why no such file or directory?

same things happend when install zlib 
cp zlib.h zconf.h /usr/local/include
chmod 644 /usr/local/include/zlib.h /usr/local/include/zconf.h
chmod: changing permissions of `/usr/local/include/zlib.h': No such file or directory
chmod: changing permissions of `/usr/local/include/zconf.h': No such file or directory
make: *** [install] Error 1

---

### Post by Pro-reason on 2008-10-18
Looking, at my own installation, I have libsdl1.2debian-alsa installed, and it provides the file /usr/lib/libSDL-1.2.so.0.11.1, not /usr/local/lib/libSDL.a.  I'm not sure why the source code that you are attempting to compile is looking for that file in that location exactly.

You need to look for something that will fulfil that dependency.

---

### Post by alienexplorers on 2008-10-18
Did you run SUDO in front of make install:
> sudo make install

---

### Post by jimmerlin on 2008-10-20
i used sudo,i even used root terminal!!

it doen't work!

so i used make install instead of check install!

and it worked!!

something wrong with check install??

---

### Post by andrew.46 on 2008-11-21
Hi,

Until checkinstall is fixed you will need:

```
sudo checkinstall -D --fstrans=no --install=yes 
```

  Andrew

---

