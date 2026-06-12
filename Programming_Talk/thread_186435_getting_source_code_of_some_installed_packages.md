---
title: "getting source code of some installed packages"
date: 2006-06-01
forum: Programming Talk
---

### Post by earthvisitor on 2006-06-01
Hi,
I want to obtain exact same version of source code tarballs (including Ubuntu patches) of some installed packages. I can't see an option for this in synaptic. How can i do that? Specifically, I am after xfdesktop sources from Xfce package. It has some problems on Xubuntu, and I want to check its sources against the SVN sources from the upstream.
Thank you.
N.

---

### Post by kh4nh on 2006-06-01
type this in terminal:

sudo apt-get source *package name*

apt-get will download the source code to the current directory that you are in. good luck

---

### Post by earthvisitor on 2006-06-02
Thank you!

---

### Post by simplyw00x on 2006-06-02
You don't need sudo; doing it with sudo will screw up permissions.
```
apt-get source <packagename>
```
on its own is better.

Also, beware. If you installed an old version, a version from a .deb or version from a repo that you no longer have in your list, it will always fetch the most recent repo (and hence in these cases, **wrong** version)

---

