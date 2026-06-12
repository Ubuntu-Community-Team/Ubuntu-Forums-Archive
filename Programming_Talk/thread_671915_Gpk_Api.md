---
title: "Gpk Api"
date: 2008-01-19
forum: Programming Talk
---

### Post by dosh on 2008-01-19
I am interested at looking at some of the GDK source code and wondering where I could download it. I have the headers but not the code is it written in C like GTK?

---

### Post by geraldm on 2008-01-19
yes
[http://www.gtk.org](http://www.gtk.org)

Gerald

---

### Post by H264 on 2008-01-19
You can the the source code for any program available in apt with apt-get source <package>
While I was checking to make sure I was right, I found the package [http://packages.ubuntu.com/gutsy/x11/gtk2.0-examples](http://packages.ubuntu.com/gutsy/x11/gtk2.0-examples) GTK2.0-examples... probably some useful stuff there too.

```
apt-get source libgtk2.0-0
```
to get the GTK2 source that is in your sources.list. It will save the source in your home folder, which can probably be changed, but I don't know how.

---

