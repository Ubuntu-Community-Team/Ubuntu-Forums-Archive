---
title: "Where to download source of gnome-appearance-properties"
date: 2008-06-04
forum: New to Ubuntu
---

### Post by mevets on 2008-06-04
I am having trouble finding the packages to download the source of gnome-appearance-properties. I tried searching for it on the ubuntu package search website but I could not find it. So I figured that it might be packaged with gnome-desktop, but it was not or I cannot find it in the downloaded tarball. Can someone direct me in the right direction?

---

### Post by wdaniels on 2008-06-04
You can use the [package search]("http://packages.ubuntu.com/search?searchon=contents&keywords=gnome-appearance-properties&mode=exactfilename&suite=hardy&arch=any") to find things like this - you will see here that it is provided by the package gnome-control-center, and you can get the source for that using:

```
apt-get source gnome-control-center
```

(the source will be downloaded into the current directory)

---

### Post by mevets on 2008-06-04
thanks, after I downloaded the soruce I noticed it was in gnome-control-center-2.22.1/capplets.

---

