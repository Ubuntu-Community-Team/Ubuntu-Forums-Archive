---
title: "Cross Compiling"
date: 2006-04-17
forum: Programming Talk
---

### Post by albinoloverats on 2006-04-17
I'm having some trouble compiling a GTK application for Windows.  I've installed the Mingw32 packages from the repositories, but can't get i586-mingw32msvc-gcc to use all the needed libraries, etc.

Anyone know what else do I need to do?

---

### Post by MichaelZ on 2006-04-17
Hello,

May be this could help:

[http://rooster.stanford.edu/~ben/linux/cross.php]("http://rooster.stanford.edu/%7Eben/linux/cross.php")
[http://rooster.stanford.edu/~ben/linux/crosshowto.php]("http://rooster.stanford.edu/%7Eben/linux/crosshowto.php")

Best wishes,
Michael

---

### Post by MichaelZ on 2006-04-17
This could help too:

[http://www.wxwidgets.org/wiki/index.php/Cross-Compiling_Under_Linux]("http://www.wxwidgets.org/wiki/index.php/Cross-Compiling_Under_Linux")

Best wishes,
Michae

---

### Post by albinoloverats on 2006-04-18
I've tried what was said on [COLOR=Red][http://www.wxwidgets.org/wiki/index....ng_Under_Linux]("http://www.wxwidgets.org/wiki/index.php/Cross-Compiling_Under_Linux")[/COLOR] and can export the variables and can configure ok, but when I try and make it returns an error:```
/usr/lib/gcc/i586-mingw32msvc/3.4.2/../../../../i586-mingw32msvc/bin/ld: cannot find -lgtk-x11-2.0
collect2: ld returned 1 exit status
``` [COLOR=Black]Any ideas?[/COLOR]

---

### Post by MichaelZ on 2006-04-18
[quote=albinoloverats]```
/usr/lib/gcc/i586-mingw32msvc/3.4.2/../../../../i586-mingw32msvc/bin/ld: cannot find -lgtk-x11-2.0
``` [COLOR=Black]Any ideas?[/COLOR][/quote] 
It seems to me that you are missing a library. Try to install it and retry.

Best wishes,
Michael

---

### Post by Kimm on 2006-04-28
> 
/usr/lib/gcc/i586-mingw32msvc/3.4.2/../../../../i586-mingw32msvc/bin/ld: cannot find **-lgtk-x11-2.0**


Surely you should use the windows libraries and not the ones for X11??!

---

