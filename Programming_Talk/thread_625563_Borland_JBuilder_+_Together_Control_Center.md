---
title: "Borland JBuilder + Together Control Center"
date: 2007-11-28
forum: Programming Talk
---

### Post by kzimir on 2007-11-28
Hey.

did anybody tried to install borland jbuilder and together? i need them for a study.

jbuilder: i get the install screen of jbuilder but clicking does nothing. when i run the install directly from the commandline i get errors about missing libc.so.6. which is actually installed. 
```
dirname: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
/bin/ls: error while loading shared libraries: librt.so.1: cannot open shared object file: No such file or directory
basename: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
dirname: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
basename: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
rm: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
```
```
$ locate libc.so
/lib32/libc.so.6
/lib/libc.so.6
/usr/lib/libc.so
```

with together i dont get any visual feedback and when running from commandline i get a missing libjava.so, which also is there!
```
Error: can't find libjava.so.
```
```
$ locate libjava.so
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/amd64/libjava.so
```


note: i run 64bit and i have jbuilder8 and together 6.1

---

