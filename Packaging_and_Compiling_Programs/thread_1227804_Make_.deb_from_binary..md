---
title: "Make .deb from binary."
date: 2009-07-31
forum: Packaging and Compiling Programs
---

### Post by eXeC001er on 2009-07-31
Please help me.
I have binary programm without source code. I need to build .deb for this binary programm for upload to my repository.
I tried to build .deb:
dpkg-deb --build 

but i need dsc, changelog and other files for repository.

---

### Post by s3a on 2009-07-31
I'm trying to learn myself as we speak but a .deb is a binary. What you're asking is to convert upstream source to a .deb.

1) Put the folder on your desktop
2) cd Destop/**foldername**
3) sudo apt-get install dh-make
4) dh_make --createorig
5) dpkg-buildpackage

The instructions should be something like that. I am a little confused as to what needs to happen between step 4 and 5 myself and wish someone could explain that to me. You can read the "Debian Maintainer's Guide" although that isn't designed for newbies.

---

### Post by Katalog on 2009-07-31
Have you checked out the [Packaging Guide]("https://wiki.ubuntu.com/PackagingGuide/Complete") on the Ubuntu Wiki yet?

---

