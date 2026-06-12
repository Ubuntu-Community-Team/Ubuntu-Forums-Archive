---
title: "apt-build unable to find 'ld'"
date: 2006-01-31
forum: Programming Talk
---

### Post by tribut on 2006-01-31
Hi.

I've been trying to recompile libtunepimp2c2 to get mp3-support. So I thought I might try out apt-build:
```
apt-build --reinstall install libtunepimp2c2
```
Having resolved the dependencies using pbuilder I get this error:
```
CC="cc" CXX="g++" CFLAGS="-g -Wall -O2" CXXFLAGS="-g -Wall -O2" /var/cache/apt-build/build/libtunepimp-0.3.0/./configure  --build=i486-linux-gnu --prefix=/usr --includedir="\${prefix}/include" --mandir="\${prefix}/share/man" --infodir="\${prefix}/share/info" --sysconfdir=/etc --localstatedir=/var --libexecdir="\${prefix}/lib/libtunepimp" --srcdir=. --disable-maintainer-mode
[...]
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.
```
I looked into config.log and that's what I found:
```
configure:2379: cc -g -Wall -O2 -Wall -g  -Wall -g  conftest.c  >&5
`-mcpu=' is deprecated. Use `-mtune=' or '-march=' instead.
collect2: cannot find 'ld'
```
The strange thing is, configure works fine if call it manually using the exact same command as above from /var/cache/apt-build. Actually, compiling it the "classic" way worked perfectly:
```
apt-get source libtunepimp2c2
cd libtunepimp-0.3.0/
dpkg-buildpackage -rsudo -D
```
Which means apt-build seems to have some environment-related problems. Why? Any idea how to resolve it?

tia,
felix

---

