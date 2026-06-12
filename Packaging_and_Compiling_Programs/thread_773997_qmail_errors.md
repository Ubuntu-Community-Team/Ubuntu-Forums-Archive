---
title: "qmail errors"
date: 2008-04-29
forum: Packaging and Compiling Programs
---

### Post by RHAnthony on 2008-04-29
I'm struggling to get an MTA setup and working on my new server.
I had help in the past getting qmail going on another box, and to be honest I'm not all that great with the whole "compiling" stuff..
Here's what I'm getting right now:

```

root@AEGIS:/usr/local/src/qmail-1.03# make setup check
./load auto-str substdio.a error.a str.a
/usr/bin/ld: errno: TLS definition in /lib/libc.so.6 section .tbss mismatches non-TLS reference in substdio.a(substdo.o)
/lib/libc.so.6: could not read symbols: Bad value
collect2: ld returned 1 exit status
make: *** [auto-str] Error 1
root@AEGIS:/usr/local/src/qmail-1.03#

```

I've already done:

```

apt-get install build_essential

```

thoughts?

---

