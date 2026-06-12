---
title: "Advice wanted relating file compression &amp; C"
date: 2008-09-16
forum: Programming Talk
---

### Post by Amon_Re on 2008-09-16
Hi guys,

I'm planning on using a zip file as a container for my app's datafiles, as each "project" contains multiple files.

At the moment i still do this by calling plain old zip to zip the directory i created which contain my files, but i'd like to handle such a thing myself.

Basicly, my requirements are:
- Ability to create a compressed file of type XYZ
- Ability to copy files into this compressed file or ability to create files within the compressed file directly.

Since i've never actually done such a thing, and there are about as many compression schemes as there are linux distro's i'm kinda at a loss of where to start, any advice would be welcome :)

---

### Post by cb951303 on 2008-09-16
[http://www.zlib.net/](http://www.zlib.net/) you can use this library. but it's pretty low level so you have to code your own routines

---

### Post by Amon_Re on 2008-09-17
> **cb951303 said:**
> [http://www.zlib.net/](http://www.zlib.net/) you can use this library. but it's pretty low level so you have to code your own routines

Another one is libzip ([http://www.nih.at/libzip/]("http://www.nih.at/libzip/")) that one comes pretty close to what i'm looking for, but their site is down atm :(

I'll look some more, rather take some extra time going through multiple libraries than having to rewrite a whole portion of code in afew months :lolflag:

---

