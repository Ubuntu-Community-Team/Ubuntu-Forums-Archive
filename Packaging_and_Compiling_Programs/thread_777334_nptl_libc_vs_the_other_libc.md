---
title: "nptl libc vs the other libc"
date: 2008-05-01
forum: Packaging and Compiling Programs
---

### Post by boondie on 2008-05-01
Hi,

I would appreciate if somebody can enlighten me on why /usr/libc.so exists separately from /lib/tls/i686/cmov/libc.so

I know that tls-related libraries are nptl. The same functions seem to exist in /lib/libc.so including pthread-related functions.

Is /lib/libc.so based on linuxthreads ?

How can I use nptl-related libraries along with other libraries in /lib for my applications development instead of the other libc ?

Thanks !!
Boondie

---

