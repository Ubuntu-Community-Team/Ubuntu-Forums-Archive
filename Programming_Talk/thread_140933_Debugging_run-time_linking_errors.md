---
title: "Debugging run-time linking errors"
date: 2006-03-07
forum: Programming Talk
---

### Post by playmesumch00ns on 2006-03-07
On the fedora boxes I use at work, when the linker cannot find a shared library (because the LD_LIBRARY_PATH does not include it), it prints out a handy message like:
```

error while loading shared libraries: libMyLib.so: cannot open shared object file: No such file or directory

```
before the program even starts up. On Ubuntu Breezy at home, I just get errors about undefined symbols during program execution. Is there a way to enable the behaviour above, as it's a lot easier to tell what's going on.


Also, on fedora if I:
```

# In tcsh
setenv LDDEBUG files

```
I get a very handy (but very verbose) output of everything the linker's doing when a program runs. This is essential for trying to debug linking errors in my shared libraries, but I can seem to get the same behaviour on ubuntu. I tried:
```

#in bash
export LDDEBUG=files

```
But I dont get any output...

---

### Post by toojays on 2006-03-07
It should be LD_DEBUG (i.e. with an underscore).

---

