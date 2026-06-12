---
title: "Compile ubuntu packages with -march=nocona"
date: 2007-08-16
forum: Programming Talk
---

### Post by chrisstankevitz on 2007-08-16
Hello Ubunto devs,

Please compile all packages with -march=nocona

OR

Please let me know how I can recompile all my packages with -march=nocona

Thank you,

Chris

---

### Post by strider1551 on 2007-08-16
> Hello Ubunto devs,
Please compile all packages with -march=nocona
I'm not a dev, and have no official association with Ubuntu, but that's not going to happen.

> Please let me know how I can recompile all my packages with -march=nocona
Now that I can do!  You will have to set the necessary flags, of course, and then use apt-get to build from source.  As root:

```
export CFLAGS="-march=nocona"
export CXXFLAGS="-march=nocona"
export MAKEOPTS="-j3"
apt-get build-dep packagename
apt-get -b source packagename
dpkg -i *.deb
```
This will download source files to the folder you are in, so I recommend doing this in a temporary folder that you can delete afterwards.

---

### Post by chrisstankevitz on 2007-08-17
Looks like a piece of cake, thanks for the quick reply!

Chris

---

