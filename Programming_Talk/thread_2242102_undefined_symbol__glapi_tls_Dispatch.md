---
title: "undefined symbol: _glapi_tls_Dispatch"
date: 2014-08-30
forum: Programming Talk
---

### Post by MikeCyber on 2014-08-30
Hi
I get as below. Any help? Thanks

michael@michael-ubuntu:~$ maya

libGL error: dlopen /usr/lib/x86_64-linux-gnu/dri/swrast_dri.so failed (/usr/lib/x86_64-linux-gnu/dri/swrast_dri.so: undefined symbol: _glapi_tls_Dispatch)
libGL error: dlopen ${ORIGIN}/dri/swrast_dri.so failed (/usr/lib/x86_64-linux-gnu/dri/swrast_dri.so: undefined symbol: _glapi_tls_Dispatch)
libGL error: dlopen /usr/lib/dri/swrast_dri.so failed (/usr/lib/dri/swrast_dri.so: cannot open shared object file: No such file or directory)
libGL error: unable to load driver: swrast_dri.so
libGL error: failed to load driver: swrast
mental ray for Maya 2014 
mental ray: version 3.11.1.4, Jan 25 2013, revision 189569

maya encountered a fatal error

Signal: 11 (Unknown Signal)
Fatal Error. Attempting to save in /usr/tmp/michael.20140830.1908.ma
michael@michael-ubuntu:~$

---

