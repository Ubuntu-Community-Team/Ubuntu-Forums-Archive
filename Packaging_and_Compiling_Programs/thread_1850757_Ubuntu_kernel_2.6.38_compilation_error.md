---
title: "Ubuntu kernel 2.6.38 compilation error"
date: 2011-09-27
forum: Packaging and Compiling Programs
---

### Post by zonemax02 on 2011-09-27
Compilation error when compiling kernels 2.6.35 / 2.6.38 on Ubuntu PC:
```
$ sudo make defconfig 
$ sudo make bzImage 
$ sudo make modules
```Results with:
```
ubuntu/ndiswrapper/iw_ndis.c:1966: error: unknown field ‘num_private’ specified in initializer 
ubuntu/ndiswrapper/iw_ndis.c:1966: warning: initialization makes pointer from integer without a cast 
ubuntu/ndiswrapper/iw_ndis.c:1967: error: unknown field ‘num_private_args’ specified in initializer 
ubuntu/ndiswrapper/iw_ndis.c:1967: warning: excess elements in struct initializer ubuntu/ndiswrapper/iw_ndis.c:1967: warning: (near initialization for ‘ndis_handler_def’) ubuntu/ndiswrapper/iw_ndis.c:1970: error: unknown field ‘private’ specified in initializer ubuntu/ndiswrapper/iw_ndis.c:1970: warning: initialization makes integer from pointer without a cast 
ubuntu/ndiswrapper/iw_ndis.c:1970: error: initializer element is not computable at load time 
ubuntu/ndiswrapper/iw_ndis.c:1970: error: (near initialization for ‘ndis_handler_def.num_standard’) 
ubuntu/ndiswrapper/iw_ndis.c:1971: error: unknown field ‘private_args’ specified in initializer 
ubuntu/ndiswrapper/iw_ndis.c:1971: warning: initialization from incompatible pointer type 
make[2]: *** [ubuntu/ndiswrapper/iw_ndis.o] Error 1 make[1]: *** [ubuntu/ndiswrapper] Error 2 
make: *** [ubuntu] Error 2

```Any ideas how to solve this compilation problem?

---

