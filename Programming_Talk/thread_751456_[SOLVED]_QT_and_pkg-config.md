---
title: "[SOLVED] QT and pkg-config"
date: 2008-04-10
forum: Programming Talk
---

### Post by StOoZ on 2008-04-10
hello developers!

I've installed the latest QT from source, now all the .pc files are installed in :
> /usr/local/Trolltech/Qt-4.3.4/lib/pkgconfig
but thats not good, since whenever I use :
> pkg-config --list-all
the QT is not listed, not I can get info for each and individual .pc file from the QT by going to its location, but I want it to be like the rest of the files, which are located :
> /usr/lib/pkgconfig
I tough of just copying them to there, but I think there a some variables to change, which I dont know how.

---

### Post by WW on 2008-04-10
You can add to the pkg-config search path with the environment variable PKG_CONFIG_PATH. E.g:
[php]
$ export PKG_CONFIG_PATH=$PKG_CONFIG_PATH:/usr/local/Trolltech/Qt-4.3.4/lib/pkgconfig
[/php]

---

### Post by keratos on 2008-04-10
or you could have changed the --prefix when installing!

---

### Post by StOoZ on 2008-04-10
Thank you both!!

---

### Post by keratos on 2008-04-12
did it work. if so how about closing the thread.

---

