---
title: "Audacity 1.3.2 + wxWidgets 2.6.4: libwx_gtk2_xrc-2.6.so.0 not found"
date: 2007-04-09
forum: Packaging and Compiling Programs
---

### Post by elreteipos on 2007-04-09
I compiled wxWidgets 2.6.4 (wxGTK) and Audacity 1.3.2 from source without any errors but when I execute *audacity*, I get this error:> audacity: error while loading shared libraries: libwx_gtk2_xrc-2.6.so.0: cannot open shared object file: No such file or directory

---

### Post by 2beers on 2007-04-11
Install the lib's named on [this site](http://wiki.ubuntuusers.de/Audacity?highlight=%28audacity%29#head-abf79c4a1dc431833b11f3ca304fc6718efbaed9) where it says "beta-version"
It's the german ubuntu forum - but the lib's u need should b the same :-)

---

### Post by elreteipos on 2007-04-12
Nevermind, I solved my own a few days ago. Here's what I had to do to fix it:> sudo ln /usr/local/lib/libwx* /lib/
sudo ldconfigIn other words: I had to symlink the libwxGTK libraries.

---

