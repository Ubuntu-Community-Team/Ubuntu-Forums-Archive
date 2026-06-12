---
title: "32 bit libs install automatically on 64 bit?"
date: 2011-07-28
forum: Packaging and Compiling Programs
---

### Post by OneOfMany07 on 2011-07-28
I'm working on a 32 bit app that I compile on my 64 bit box.  This has worked OK with the g++/gcc multilib packages installed, until I just added a new library.  I thought Ubuntu would install both 32 and 64 bit versions when I installed the dev package, but that seems to not be the case (libmxml).

I did manage to find an old script (getlibs) that can help download the needed parts, but is this still necessary?  It was in [http://ubuntuforums.org/showthread.php?t=474790]("http://ubuntuforums.org/showthread.php?t=474790").

This seems like something that should have a single meta package that triggers all the other work (like "compile-for-32-bit" or something).

Or is there an even easier way I don't know about?

Thanks for your time,
Joe

---

### Post by MadCow108 on 2011-07-29
the easier way is being worked on but its only half ready.
see:
[http://wiki.debian.org/Multiarch/Implementation](http://wiki.debian.org/Multiarch/Implementation)
[https://wiki.ubuntu.com/MultiarchCross](https://wiki.ubuntu.com/MultiarchCross)
only few libraries have already been converted yet.

until its ready the easiest way is probably setting up a chroot for the other arch and compiling there:
[https://wiki.ubuntu.com/PbuilderHowto](https://wiki.ubuntu.com/PbuilderHowto)

---

