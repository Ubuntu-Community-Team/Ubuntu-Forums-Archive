---
title: "Run Apache2 (or anything) on Edgy with LD_ASSUME_KERNEL=2.4.19"
date: 2006-11-09
forum: Programming Talk
---

### Post by ashayh on 2006-11-09
Hi

Is there any way to run Apache2 with:```
LD_ASSUME_KERNEL=2.4.19
``` 

I add LD_ASSUME_KERNEL=2.4.19 to the apache2 init.d script. When I do that, I get this error:

```
/bin/sh: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
```

The library does exist, and the same works fine on Debian 3.1 r3, which come with 2.4 kernel and non-NPTL library.

Also, if I set this env variable on the cmd line shell by:  ```
export LD_ASSUME_KERNEL=2.4.19
``` no command works. They all give similar library errors.

This also works fine on RHEL4 with 2.6 kernel after installing older non-NPTL library.

Is there any way to do this on Edgy? The reason being I have a closed-source Apache module that has this hard-coded requirement.

Any pointers are appreciated.
Thanks

---

### Post by ciscosurfer on 2006-11-09
I'd ask the coder of the module to update it to reflect newer kernel advancements.

---

