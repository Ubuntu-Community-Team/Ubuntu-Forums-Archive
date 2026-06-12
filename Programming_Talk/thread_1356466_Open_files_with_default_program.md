---
title: "Open files with default program"
date: 2009-12-16
forum: Programming Talk
---

### Post by inzpektor on 2009-12-16
I'm making a Java-app that should be able to open different files using the users preferred application for that particular filetype.  For example, if the user has set "Open with" in Nautilus for .odt files to oowriter then that program should be used to open the file.

In Windows, you can just call Runtime.exec("document.odt"); and the OS will recognize that this file is not executable and instead launch the program associated with this file-type.  In Mac OSX (I've been told), you should call Runtime.exec("open document.odt");

But what do I do in Linux?  Of course, the best thing would be to reuse the Nautilus filetype associations (the "Open with"-tab) - if the current X-session is running Gnome, and Konqueror's ditto if we're in KDE etc.

Is there a program like this available?

---

### Post by ssam on 2009-12-16
```

xdg-open document.odt

```

from [http://portland.freedesktop.org/wiki/](http://portland.freedesktop.org/wiki/) should be installed on all ubuntu, and most linux.

PS:
i have
```

alias o="xdg-open"

```
in my bashrc, so that from bash i can do
```

o filename

```

---

### Post by inzpektor on 2009-12-16
> **ssam said:**
> ```

xdg-open document.odt

```


Many thanks!  It works like a charm.  That was exactly what I was looking for.

---

