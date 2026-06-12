---
title: "Question??"
date: 2008-08-27
forum: New to Ubuntu
---

### Post by eng.ahmed on 2008-08-27
dear my friends ,


i'm beginner on ubuntu and ineed help


How can iget the source code of any programe on linux ubuntu?

plz give me an exampla?:KS

---

### Post by kellemes on 2008-08-27
> **eng.ahmed said:**
> dear my friends ,


i'm beginner on ubuntu and ineed help


How can iget the source code of any programe on linux ubuntu?

plz give me an exampla?:KS

Why do you need to sourcecode of any program if I may ask?
Is there something specific you want to do?

---

### Post by Nepherte on 2008-08-27
```
sudo apt-get source <program>
```

This is the man page for apt-get source:
```
source
           source causes apt-get to fetch source packages. APT will examine
           the available packages to decide which source package to fetch. It
           will then find and download into the current directory the newest
           available version of that source package. Source packages are
           tracked separately from binary packages via deb-src type lines in
           the sources.list(5) file. This probably will mean that you will not
           get the same source as the package you have installed or as you
           could install. If the --compile options is specified then the
           package will be compiled to a binary .deb using dpkg-buildpackage,
           if --download-only is specified then the source package will not be
           unpacked.

           A specific source version can be retrieved by postfixing the source
           name with an equals and then the version to fetch, similar to the
           mechanism used for the package files. This enables exact matching
           of the source package name and version, implicitly enabling the
           APT::Get::Only-Source option.

           Note that source packages are not tracked like binary packages,
           they exist only in the current directory and are similar to
           downloading source tar balls.
```

---

