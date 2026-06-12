---
title: "How to locate patch rejects file?"
date: 2012-08-21
forum: Packaging and Compiling Programs
---

### Post by Vadi on 2012-08-21
I'm having an error applying some patches when using debuild:

```
dpkg-source: info: using source format `3.0 (quilt)'
dpkg-source: info: building mudlet using existing ./mudlet_2.0-rc12.orig.tar.gz
patching file src/src.pro
Hunk #1 FAILED at 8.
Hunk #2 succeeded at 27 (offset 1 line).
Hunk #3 succeeded at 243 (offset 3 lines).
1 out of 3 hunks FAILED -- saving rejects to file src/src.pro.rej
dpkg-source: error: LC_ALL=C patch -t -F 0 -N -p1 -u -V never -g0 -E -b -B .pc/project_file/ < mudlet-2.0-rc12.orig.s5Vaub/debian/patches/project_file gave error exit status 1

```

... however there is no src/src.pro.rej file being created. How can I obtain it?

---

### Post by SevenMachines on 2012-08-22
I'd have thought it was but anyway, if it exists anywhere in the source tree then

```
$ find ./ -name '*.rej'
```

---

### Post by Vadi on 2012-08-22
Not sure why, it really is not there:

```
1 out of 2 hunks FAILED -- saving rejects to file src/mudlet-lua/lua/LuaGlobal.lua.rej
dpkg-source: error: LC_ALL=C patch -t -F 0 -N -p1 -u -V never -g0 -E -b -B .pc/luaglobal_path/ < mudlet-2.0-rc12.orig.BCgePM/debian/patches/luaglobal_path gave error exit status 1
dpkg-buildpackage: error: dpkg-source -b mudlet-2.0-rc12 gave error exit status 2
debuild: fatal error at line 1350:
dpkg-buildpackage -rfakeroot -d -us -uc -S -sa failed
vadi@gooseberry:~/Desktop/ppa/mudlet-2.0-rc12$ find ./ -name '*.rej'
vadi@gooseberry:~/Desktop/ppa/mudlet-2.0-rc12$ 
```

I've worked out the real issue here though and am updating patches now to make it work.

---

