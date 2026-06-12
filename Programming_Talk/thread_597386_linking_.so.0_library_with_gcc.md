---
title: "linking .so.0 library with gcc"
date: 2007-10-30
forum: Programming Talk
---

### Post by turbopeppe on 2007-10-30
hi everyone,
i am using eclipse to compile my own c source file, which makes use of some functions contained in .so libraries. I use gcc's -l option to specify libraries' names and -L to include the path where they are. Everything works fine for .so libraries, but when i try to specify libhdf5.so.0 in gcc's  -lhdf5 option, I get a "ld: cannot find -lhdf5" error, even if the path is right...how can I make things work? Thanks in advance

---

### Post by hod139 on 2007-10-30
Is libhdf5.so.0 in a standard library location, or are you using -L to specify the location?  If you put it into a standard location and -l cannot find it, you may need to run
```

sudo ldconfig

```
to update LD's cache of libraries.

---

### Post by turbopeppe on 2007-10-31
I use -L to specify the location. Once this done, I use -l to specify the library's name. But using the -l<name> option results in lib<name>.so being linked, while I need to link libhdf5.so.0 which is not recognized by the -l option. How can I resolve this problem? Thanks in advance!!!

---

### Post by Compyx on 2007-10-31
You should be fine with -lhdf5, on my system libhfd5.so is symlinked to libhfd5-1.6.5.so.0.0.0. This is quite common, you link with a library without specifying the version and symlinks take care of the actual version needed to link to.

---

