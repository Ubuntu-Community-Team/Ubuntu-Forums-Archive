---
title: "problems with basic compile"
date: 2005-12-22
forum: Packaging and Compiling Programs
---

### Post by kpd on 2005-12-22
hi,

i'm running 5.10 server (2.6.12-9-amd64-k8-smp), and everything seems ok, except i'm unable to build relatively non-troublesome programs from source. i'm trying to compile pvm3, but it barfs errors like 
```
error: array type has incomplete element type
```
and 
```
warning: incompatible implicit declaration of built-in function ‘strcpy’
```
i've installed build-essential-- what should i check next?

thanks,
k

---

### Post by kpd on 2005-12-22
update:

well, i was able to compile and run a version of the byte unix benchmark suite, but it threw lot of warnings like:

```
warning: incompatible implicit declaration of built-in function [etc...]
```

is this just caused by the code not being compatible with gcc 4.0? any tips on how to investigate further?

---

