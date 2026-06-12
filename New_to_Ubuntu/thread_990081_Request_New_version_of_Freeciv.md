---
title: "Request: New version of Freeciv"
date: 2008-11-22
forum: New to Ubuntu
---

### Post by aaeeiio on 2008-11-22
I'd be really happy if Freeciv was updated to 2.1.6 in the repository, since I can't install it manually and all the multiplayer games are in the latest version.

Please? :)

---

### Post by Sef on 2008-11-22
1) Moved to Absolute Beginners.

2) What problems do you have installing it?

---

### Post by aaeeiio on 2008-11-23
I downloaded the freeciv-2.1.6.tar.gz package and unpacked it and then typed "./configure" in the appropriate directory. After going on for a while it gives the following error:

```
checking for GTK+ - version >= 2.4.0... no
*** Could not run GTK+ test program, checking why...
*** The test program failed to compile or link. See the file config.log for the
*** exact error that occured. This usually means GTK+ is incorrectly installed.
configure: WARNING: Not checking for SDL; use --enable-client=sdl to enable
checking for X... libraries , headers 
checking whether Xfuncproto was supplied... no, found:  FUNCPROTO=15 NARROWPROTO
checking pkg-config is at least version 0.9.0... yes
configure: WARNING: Not checking for XAW; use --enable-client=xaw to enable
configure: error: could not guess which client to compile
```

... and the configure process ends.

---

### Post by zvacet on 2008-11-23
Maybe [this]("http://freeciv.wikia.com/index.php?title=Forum:Compiling_source_on_ubuntu_-_cant_find_sdl&t=20080825011157") will help you.

---

### Post by aaeeiio on 2008-11-23
zvacet: I don't understand how the link's issue relates to mine.

---

### Post by zvacet on 2008-11-24
It shows how to compile that package.

---

### Post by hyper_ch on 2008-11-24
if you're on hardy have a look here: [http://www.playdeb.net/](http://www.playdeb.net/)

---

### Post by aaeeiio on 2008-11-24
> **hyper_ch said:**
> if you're on hardy have a look here: [http://www.playdeb.net/](http://www.playdeb.net/)

Oh my. It works.
Thank you!

---

