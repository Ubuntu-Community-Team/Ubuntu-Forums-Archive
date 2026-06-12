---
title: "Error compiling FUSE 2.8.5 Under Ubuntu 10.04"
date: 2010-12-18
forum: Packaging and Compiling Programs
---

### Post by e-blade on 2010-12-18
I've been at it for some time and my limited knowledge of Linux is now used up.

I've downloaded Fuse 2.8.5 from [http://sourceforge.net/projects/fuse/files/fuse-2.X/]("http://sourceforge.net/projects/fuse/files/fuse-2.X/")

Unpacked it and aimed to run ./configure; make; make install.

Now from what I can tell the configure goes fine, but the make fails horribly with the following message:

fuse.c:3967: fatal error: opening dependency file .deps/fuse.Tpo: Permission denied

Now to my mind that means that I might be able to chmod the file and everything should be dandy. Unfortunately the file doesnt seem to exist on my drive (not found through locate or find) which begs the question:

What on earth do I need to do to fix this?

---

