---
title: "Compiling cheese dev branch gnome-3-2"
date: 2012-11-15
forum: Packaging and Compiling Programs
---

### Post by delioda on 2012-11-15
Hi,
I tried to install cheese from git development branch gnome-3-2 but after lunching:
sh autogen.sh
make
make install

if I try to lunch the program with the command:
cheese

I receive this error:
cheese: error while loading shared libraries: libcheese.so.1: cannot open shared object file: No such file or directory


But if I do whereis libcheese.so.1 I receive:
libcheese.so: /usr/local/lib/libcheese.so.1 /usr/local/lib/libcheese.so

so it does exist but.......cheese doesn't fnd it. Does anybody know what's the problem?
Mind that I'm trying to study the code of cheese so I'm not just interested in having the software installed, I want to be able to modify and recompile it.
Thanks

---

### Post by MadCow108 on 2012-11-15
you probably have to set LD_LIBRARY_PATH to contain /usr/local/lib:

```
export  LD_LIBRARY_PATH=${LD_LIBRARY_PATH+$LD_LIBRARY_PATH:}/usr/local/lib
```

or configure it system wide in /etc/ld.so.conf.d

---

### Post by delioda on 2012-11-15
Yes it works thank you, loads of warning about gtk types when I run it but here  will start my job: to fix them ;)

---

