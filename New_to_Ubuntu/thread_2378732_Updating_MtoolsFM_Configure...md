---
title: "Updating MtoolsFM Configure.."
date: 2017-11-26
forum: New to Ubuntu
---

### Post by mtcs2 on 2017-11-26
No solution found here on previous post... using Xubuntu 16.04

[https://ubuntuforums.org/showthread.php?t=1166556](https://ubuntuforums.org/showthread.php?t=1166556)

...
checking for GTK - version >= 1.2.0... no
*** The gtk-config script installed by GTK could not be found
*** If GTK was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the GTK_CONFIG environment variable to the
*** full path to gtk-config.
configure: error: MToolsFM needs GTK+ V1.2 or better

I couldn't find a GTK_CONFIG variable or file and CATFISH search is fruitless so far.

Entries in my ENV'VAR'S are:

GTK_IM_MODULE=
GTK_OVERLAY_SCROLLING=0

Path should be added /usr/lib/i386-linux-gnu/gtk-2.0/2.10.0/? I don't think so... but still looking.


I am looking for some insight how to modify CONFIGURE or fulfill proper PATH. 

"Need help!" - The Matrix

---

### Post by Holger_Gehrke on 2017-11-26
You're trying to compile a program that has not had any maintenance since 2008. The program is looking for configuration tools for a library that had two major version jumps since then. The absence of gtk-config (a tool that tells compilers and linkers where to find the headers and libraries for gtk 1.2) should be taken as a hint that programs that depend on gtk 1.2 will need a major rewrite to work with newer versions of gtk.

Holger

---

### Post by mtcs2 on 2017-11-26
Thank you for solidifying the feeling I had into words.  Back to the command line I guess until am much much better at programming! Can't blame me for trying. Can you?

---

