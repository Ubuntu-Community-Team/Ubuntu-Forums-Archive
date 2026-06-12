---
title: "Prefix to KDE4 isntallation?"
date: 2008-06-28
forum: New to Ubuntu
---

### Post by masterjonny on 2008-06-28
I'm trying to compile the new kTorrent to run on my Ubuntu machine. I've installed kde4 and kde4 core for the libraries it need's, but I'm still a bit stuck.

On the kTorrent the instruction says "cmake -DCMAKE_INSTALL_PREFIX=/path/to/prefix/of/kde4/installation"

So I've been typing "cmake -DCMAKE_INSTALL_PREFIX=/usr/lib", but I always get the error 

```
ERROR: cmake/modules/FindKDE4Internal.cmake not found in /home/jonny/.kde4/share/apps;/usr/lib/kde4/share/kde4/apps
```

Any clues as to what path I should be typing for what I should be doing?

---

### Post by The J on 2008-07-13
Try installing the "kdelibs5-dev" package.

---

### Post by Bachstelze on 2008-07-13
> **masterjonny said:**
> On the kTorrent the instruction says "cmake -DCMAKE_INSTALL_PREFIX=/path/to/prefix/of/kde4/installation"

```
cmake -DCMAKE_INSTALL_PREFIX=`kde4-config --prefix`
```

*kde4-config --prefix* will output the installation prefix of KDE4, and the backticks are used to pass the output of a command to the shell. I wonder how KDE4 developpers can be unaware of that...

You'll also need the -dev packages indeed, but the two issues are unrelated.

---

