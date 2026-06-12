---
title: "Firefox fails because of missing LIBPK-GTK-MODULE.SO"
date: 2009-12-15
forum: Repositories &amp; Backports
---

### Post by superbiskit on 2009-12-15
Running karmic (9.10), updated as of 2009-12-14.

I see from a closed thread that this has happened to others.
SEE: <[http://ubuntuforums.org/showthread.php?t=1200986](http://ubuntuforums.org/showthread.php?t=1200986)[i seem to have deleted libpk-gtk-module.so]("http://ubuntuforums.org/showthread.php?t=1200986")>, also
[Bug #389766]("https://bugs.launchpad.net/ubuntu/+source/packagekit/+bug/389766"), which also gives a workaround.
Starting browsers, and some other apps, gives me "*GTK-message: cannot load 'pk-gtk-module.so'."  In Firefox, this is fatal!

Sadly, using "gksudo gconf-editor (or gconftool-2)", from a terminal gives a lot of bad news about "failed to connect to configuration server ..."
I'm guessing I've approached this wrong, because if I were truly unable to connect to the configuration server I suspect nothing at all would work.

So, please, **help!** TIA.

---

