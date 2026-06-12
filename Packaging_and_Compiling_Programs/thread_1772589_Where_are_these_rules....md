---
title: "Where are these rules..."
date: 2011-05-31
forum: Packaging and Compiling Programs
---

### Post by windyweather on 2011-05-31
I've seen a ton of documentation about packaging, but nothing that answers these questions. Can someone point me to these answers?

What GID/UID are package files supposed to have?
Is there an option to dpkg-deb to set them?

```
Lintian check results for /home/darrell/code_packages/coreheaterqt_1.2_all.deb:
E: coreheaterqt: wrong-file-owner-uid-or-gid usr/share/icons/hicolor/96x96/ 1000/1000
E: coreheaterqt: wrong-file-owner-uid-or-gid usr/share/icons/hicolor/96x96/apps/ 1000/1000
E: coreheaterqt: wrong-file-owner-uid-or-gid usr/share/icons/hicolor/96x96/apps/coreheaterqt.png 1000/1000
E: coreheaterqt: arch-independent-package-contains-binary-or-object usr/bin/CoreHeaterQt
```

The arch tag was set to ALL. I thought that means x86 and x64. What's the error above about? Any used for sources right? My app package is supposed to work on both x86 and x64, and the app is happy on both.

For the packages installed with the "Software Center", where is there a document that describes the rules for packages.
Where do I put the screenshot? and how big and what format? [PNG i presume].

License: ???
Updates: ???

Oh. and by the way. If the package manager happens to be open, and you try to use the software center, it looks like it just is taking forever. But of course it's locked out of the database by the package manager. Might be interesting if it popped something up saying that the database was locked instead of just sitting there. But I guess that belongs in "suggestions" or somewhere.

Is there a utility to build the MP5 or whatever signatures of all the files? Part of a package too? Any real advantage to putting these in a package for a small user application?

Thanks,

ww

---

### Post by windyweather on 2011-06-24
If you sudo - or gksudo - a package builder, then when it calls debpkg it does the right thing and sets all the files to root ownership.

Try this package builder, and read the documentation that I wrote for it, to get starting building simple packages easily.

[https://sourceforge.net/projects/debipack/](https://sourceforge.net/projects/debipack/)

Enjoy,
ww

---

### Post by gmargo on 2011-06-25
You should never use root (aka sudo etc) to compile.  Use the **fakeroot(1)** command to run your package build step.  So instead of running "dpkg-deb ....", run "fakeroot dpkg-deb ...".

I checked the **lintian(1)** source - it expects all files to be uid/gid below 100 (or certain "nobody" values), which is why it choked on your normal 1000 uid.

You may also find this informative:
[http://www.debian.org/doc/debian-policy/ch-opersys.html#s9.2](http://www.debian.org/doc/debian-policy/ch-opersys.html#s9.2)

---

