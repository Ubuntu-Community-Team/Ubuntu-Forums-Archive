---
title: "Toubles compiling from sources."
date: 2009-02-18
forum: Programming Talk
---

### Post by SplinterOfChaos on 2009-02-18
Recent Ubuntu convert (err, Xubuntu) but I've been programming a good couple of years. Thusly, I know the advantages of getting to chose how my applications compile--or at least theoretically since I'm having so much trouble doing so.

Right now, I my project is simple: Compile gpicview, optimize for my CPU arch and speed. If I can get passed that, hack a small feature into it and pretend it works. This is being made difficult by ./configure churning out this message:> checking for PACKAGE... configure: error: Package requirements (gtk+-2.0 >= 2.6.0) were not met:

No package 'gtk+-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables PACKAGE_CFLAGS
and PACKAGE_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details. It seems like just a small thing, but I haven't made much progress in this area. apt-get couldn't find me a package named gtk+-2.0, I think I might have had the sources at one point but didn't know what to do with 'em, and I don't know how to "set" the "PACKAGE_CFLAGS" and "PACKAGE_LIBS" variables. 

So, how can I compile this? What should I be learning in order to better compile programs from sources? Is there a package manager that works in sources, not binaries? I don't want to compile *everything* myself, but it'd make tracking down these dependencies a LOT easier, I'd think.

---

### Post by geraldm on 2009-02-18
Usually with gtk+ you would use a Makefile.

If you are using the command line, you need to provide the location of the package headers and libraries.  That might be  "-I/usr/include/gtk+" for some
systems.  It may be easier to use the example in package pkg-config man page,
as that should provide the information and save some typing.

gtk+-2.0 is not the easiest package to start working with, due to various other
dependency packages.

Good luck,
Gerald

---

### Post by snova on 2009-02-18
Try installing the **libgtk2.0-dev** package.

Oh, and **build-essential** if you don't have it already.

---

### Post by SplinterOfChaos on 2009-02-18
[ irrelevant stuff deleted ]

I posted how I wasn't sure, then snova's advice worked! (S/He posted between me opening the thread and clicking reply, appearance.) Thanks a lot! Hope it's smooth sailing from here.

---

