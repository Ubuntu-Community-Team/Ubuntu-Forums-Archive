---
title: "Anybody able to compile libgpod on Karmic?"
date: 2009-12-15
forum: Packaging and Compiling Programs
---

### Post by pedja_portugalac on 2009-12-15
Is there anybody able to compile latest libgpod from Git on Karmic? I am trying for few hours without success. Every time I run ./autogen.sh or ./configure I get this error:
```
checking for LIBGPOD... configure: error: Package requirements (glib-2.0 >= 2.8.0 gobject-2.0 sqlite3) were not met:

No package 'sqlite3' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables LIBGPOD_CFLAGS
and LIBGPOD_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
```
sqlite3 is already installed:
```
sqlite3 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```
I don't know how to adjust the PKG_CONFIG_PATH environment variable to compile this crap. Launchpad ppa version is little outdated. More then 6 months I can't use ipod shuffle 3g 4GB on Ubuntu, I'm not the only one, and I was wondering if they have added support for this device in the latest version from Git.
```
git clone git://gtkpod.git.sourceforge.net/gitroot/gtkpod/libgpod
```
Please, if anybody successfully compiled this on Karmic can you share here with us?

---

### Post by SevenMachines on 2009-12-15
quite confusingly, when configure says
No package 'sqlite3' found
what it actually means is it cannot find the headers for sqlite3. so the package to install is in fact libsqlite3-dev

$ sudo apt-get install libsqlite3-dev

---

### Post by pedja_portugalac on 2009-12-16
Thank you very much. It solved the problem. Still it doesn't support ipod shuffle 3G 4GB at this version but now, at least, I know how to compile and check often. Thanks ones again.

---

### Post by Floola on 2010-03-12
Floola 5.5 now supports shuffle3G.

Visit [http://www.floola.com](http://www.floola.com)

---

