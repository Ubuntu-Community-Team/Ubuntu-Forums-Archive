---
title: "Install Packages (WINE) from hard drive (not net)"
date: 2005-12-27
forum: Repositories &amp; Backports
---

### Post by mfarquhar on 2005-12-27
i have no internet connection on my linux box, but got my hands on wine packages (.deb) on their server and transferred them to the hard drive on ubuntu

i can't find out how to install them from my hard drive

iv'e tried installing them in both KDE and GNOME but no luck
synaptic doesn't work
adept doesn't work
right clicking the files and clicking install says there is an error

help me...please...

---

### Post by Koybe on 2005-12-27
Just use the dpkg command ;)

```
sudo dpkg -i yourpackage.deb
```

---

