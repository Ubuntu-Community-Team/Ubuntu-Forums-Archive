---
title: "configure: error: can't find X includes"
date: 2006-06-07
forum: Packaging and Compiling Programs
---

### Post by Nonno Bassotto on 2006-06-07
I was trying to create a deb package for KtabEdit
[http://kguitartmp.sourceforge.net/](http://kguitartmp.sourceforge.net/)
but the command "auto-apt run ./configure" ends with the line
```

checking for X... configure: error: Can't find X includes. Please check your installation and add the correct paths!

```
I don't know what I should do now. Can anybody help me? Please note that this is my first try to make a deb package, so try to explain in a simple way.

---

### Post by tonyr on 2006-06-07
The headers are in the development libraries.  Install package **libx11-dev** and try
again.  You may run into other **configure** failures like this.  The development
libraries you need may be listed in a document somewhere in the source tree, maybe
README or INSTALL,  or you may have to discover what you need as **configure**
reports failures.

---

### Post by Nonno Bassotto on 2006-06-07
after installing xlibs-dev this step goes smoothly, but now it stops at
```

checking for Qt... configure: error: Qt (>= Qt 3.2) (headers and libraries) not found. Please check your installation!

```
I have tried to install libqt3-mt-dev but I get the error
```

libqt3-mt-dev:
 Depends on: libfreetype6-dev but it is not going to be installed
 Depends on: libxft-dev but it is not going to be installed

```
(the translation is mine). The same error if I try with libqt4-dev. This must be related to the fact that I installed new libraries to get better fonts, following an howto on this forum. I don't want to screw up my installation to compile this (I already have to remove lots of things). I think I will do without.
Thank you for your help

---

