---
title: "Problem with pgi and fftw, blacs, scalapack, etc..."
date: 2006-05-03
forum: Programming Talk
---

### Post by ispmarin on 2006-05-03
Hello everybody: Some serious problems happened in my dapper system. I am trying to compile everything with pgcc, this errors appears:

/usr/bin/ld: skipping incompatible /usr/lib/libc.so when searching for -lc
/usr/bin/ld: skipping incompatible /usr/lib/libc.a when searching for -lc
/usr/bin/ld: skipping incompatible /usr/bin/../lib/libc.so when searching for -lc
/usr/bin/ld: skipping incompatible /usr/bin/../lib/libc.a when searching for -lc/usr/bin/ld: skipping incompatible /usr/lib/libc.so when searching for -lc
/usr/bin/ld: skipping incompatible /usr/lib/libc.a when searching for -lc
/usr/bin/ld: cannot find -lc

even with a test hello program. 
output dpkg -l | grep libc6:
ii  libc6                                            2.3.6-0ubuntu17            GNU C Library: Shared libraries and Timezone
ii  libc6-dev                                        2.3.6-0ubuntu17            GNU C Library: Development Libraries and Hea
ii  libc6-i386                                       2.3.6-0ubuntu17            GNU C Library: 32bit Shared libraries for am

What can be happening?  My box is a amd64 on dapper updated.

thanks

---

