---
title: "How can i find out what are the symbols in a .a file?"
date: 2008-06-28
forum: Packaging and Compiling Programs
---

### Post by yinglcs2 on 2008-06-28
Hi,

How can i find out what are the symbols defined in a .a file?

---

### Post by WW on 2008-06-28
Use the **nm** command; check the manpage for the options.

For example,
```

$ nm /usr/lib/libdl.a

dlopen.o:
                 U __dlopen
0000000000000000 n __evoke_link_warning_dlopen
0000000000000000 T dlopen

dlclose.o:
                 U __dlclose
0000000000000000 T dlclose

dlsym.o:
                 U __dlsym
0000000000000000 T dlsym

dlvsym.o:
                 U __dlvsym
0000000000000000 W dlvsym

dlerror.o:
                 U __dlerror
0000000000000000 T dlerror

dladdr.o:
                 U __dladdr
0000000000000000 T dladdr

dladdr1.o:
                 U __dladdr1
0000000000000000 T dladdr1

dlinfo.o:
                 U __dlinfo
0000000000000000 T dlinfo

dlmopen.o:
                 U __dlmopen
0000000000000000 n __evoke_link_warning_dlmopen
0000000000000000 T dlmopen
$  

```

---

### Post by Cygnus on 2008-07-07
> **WW said:**
> Use the **nm** command; check the manpage for the options.


nm -C can be nice as it writes the demangled names.

---

