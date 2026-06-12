---
title: "GTK+ Development Packages"
date: 2009-04-14
forum: Programming Talk
---

### Post by Jesdisciple on 2009-04-14
I want to use the highest and most portable GTK+ version for development and [I've been told]("http://www.gtkforums.com/viewtopic.php?t=3337") that all non-commercial distros provide 2.12+, but I can't seem to find such an package.  I checked my gtk-config, and I'm guessing that this actually means 2.10 like Java's 1.6 means 6?```
$ gtk-config --version gtk
1.2.10
```

[Here](http://packages.ubuntu.com/hardy/libgtk2.0-dev)'s the package I'm using, but I can't find an equivalent package with a higher version: [http://www.google.com/search?hl=en&q=libgtk-2.1..2.9+site%3Apackages.ubuntu.com](http://www.google.com/search?hl=en&q=libgtk-2.1..2.9+site%3Apackages.ubuntu.com)  (As Google interprets the versions as decimals, that should cover all of them.)

Can anyone give some guidance please?

---

### Post by Vadi on 2009-04-14
gtk-config?

Use *pkg-config*. gtk-config is from 1.2 series, long depreciated.

See [http://library.gnome.org/devel/gtk-tutorial/stable/x111.html](http://library.gnome.org/devel/gtk-tutorial/stable/x111.html)

---

### Post by Jesdisciple on 2009-04-14
???  I'm not sure exactly what that's telling me, but it's not the highest GTK+ version I have installed.  My best guess for how to get that didn't work:```
$ pkg-config --exact-version gtk+
Must specify package names on the command line
$ pkg-config --exact-version gtk+-2.0
Must specify package names on the command line
```

EDIT: Never mind, someone at the GTK Forums set me straight:```
$ pkg-config --modversion gtk+-2.0
2.14.4
```

Thanks.

---

### Post by Vadi on 2009-04-14
Glad you got it.

---

