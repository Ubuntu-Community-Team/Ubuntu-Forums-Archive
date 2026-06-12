---
title: "Ephiphany bug?"
date: 2008-04-30
forum: New to Ubuntu
---

### Post by Bothered on 2008-04-30
I'm getting a segmentation fault when I follow the following steps:

1. Launch ephipany
2. Select Edit->Personal Data
3. Click the "Properties" button (without selecting a cookie)

Does anyone else see this bug?

EDIT: Oops - the thread subject should be "Epiphany bug?"

---

### Post by Zalbor on 2008-04-30
Indeed, it happens.

---

### Post by hermes0710 on 2008-04-30
Try running epiphany as root. ("sudo epiphany" from terminal. does this happen too? Have you upgraded or clean installed your os?)

---

### Post by Bothered on 2008-04-30
This is a clean hardy install. I'm not keen on running a web browser as root (also, that should be "gksudo epiphany").

---

### Post by omns on 2008-04-30
Yes, I get it to on a clean install. Time to report a bug :)

---

### Post by hermes0710 on 2008-04-30
> **Bothered said:**
> This is a clean hardy install. I'm not keen on running a web browser as root (also, that should be "gksudo epiphany").

I don't suggest running it permanently as root. Only to check if this happens to root user too. "sudo" will do the work, but if you prefer gksudo, gksudo it is.

---

### Post by Bothered on 2008-04-30
Bug report submitted: [https://bugs.launchpad.net/ubuntu/+source/epiphany-browser/+bug/224684](https://bugs.launchpad.net/ubuntu/+source/epiphany-browser/+bug/224684)

I'd heard that it was a bad idea to launch GUI programs with sudo rather than gksudo:

[http://psychocats.net/ubuntu/graphicalsudo](http://psychocats.net/ubuntu/graphicalsudo)

---

### Post by omns on 2008-04-30
I also noticed that after installing Epiphany and all it's extensions that Firefox consistently began to crash. I believe the problem lay in one of the following dependencies but am unsure which one. All is well again since their removal.

gwget (0.99-2ubuntu1)
libavahi-gobject0 (0.6.22-2ubuntu4)
libosp5 (1.5.2-3ubuntu3)
w3c-dtd-xhtml (1.1-5ubuntu1)

---

### Post by bapoumba on 2008-05-01
Here is the upstream bug report for epiphany (just came across that bug, the button should be grayed out when no cookie is selected):
[http://bugzilla.gnome.org/show_bug.cgi?id=504136]("http://bugzilla.gnome.org/show_bug.cgi?id=504136")

Graphical apps should be run with gksudo indeed. It will probably work with sudo, but it is also likely to give issues with X for a regular user after.

@ omns: I run both epiphany and firefox (I had to after epiphany giving me some issues on UF) and have not seen FF crashes.

---

### Post by omns on 2008-05-09
> **bapoumba said:**
> @ omns: I run both epiphany and firefox (I had to after epiphany giving me some issues on UF) and have not seen FF crashes.

I haven't had any problems since re-installing epiphany without its extensions package

---

### Post by bapoumba on 2008-05-10
> **omns said:**
> I haven't had any problems since re-installing epiphany without its extensions package

You could try enabling the extensions one by one to see which one is giving you trouble :)

---

