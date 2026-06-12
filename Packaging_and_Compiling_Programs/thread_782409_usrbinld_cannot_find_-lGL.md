---
title: "/usr/bin/ld: cannot find -lGL"
date: 2008-05-04
forum: Packaging and Compiling Programs
---

### Post by getobox on 2008-05-04
I am trying to compile a variation of Quake 1 that has worked before on a different platform.  However, when it gets to the point of linking the program it errors out with the following message.

[INDENT]**Linking quake/qrack-glx client with flags:
-lm -pthread -ldl
-L/usr/X11R6/lib -lX11 -lXext -lXxf86vm -lXxf86dga
-L/usr/local/lib -L/usr/X11R6/lib -lGL -ljpeg -lpng12


/usr/bin/ld: cannot find -lGL
collect2: ld returned 1 exit status
make[1]: *** [quake/qrack-glx] Error 1
make: [release] Error 2 (ignored)[/INDENT]

Any ideas?

Thanks.

---

### Post by getobox on 2008-05-07
Thanks for all the responses, but I figured it out myself.  I was missing some glx dev files.

---

