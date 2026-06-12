---
title: "Anjuta 1.2.4a / gcc Problem"
date: 2006-09-06
forum: Programming Talk
---

### Post by ichigo on 2006-09-06
EDIT: problem is solved

I've installed Anjuta, gcc etc. from the repos. The installation seemed to work well. But when I try to start a new project, the autogenerating finishs unsuccessfully with the following output.
```
checking for gcc... gcc
configure: error: C compiler cannot create executables
See 'config.log' for more details
```
In the config.log there were these lines:
```

configure:2350: $? = 0
configure:2352: gcc -v </dev/null >&5
Using built-in specs.
Target: i486-linux-gnu
Configured with: ../src/configure -v --enable-languages=c,c++,java,f95,objc,ada,treelang --prefix=/usr --enable-shared --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --enable-nls --program-suffix=-4.0 --enable-__cxa_atexit --enable-clocale=gnu --enable-libstdcxx-debug --enable-java-awt=gtk-default --enable-gtk-cairo --with-java-home=/usr/lib/jvm/java-1.4.2-gcj-4.0-1.4.2.0/jre --enable-mpfr --disable-werror --with-tune=pentium4 --enable-checking=release i486-linux-gnu
Thread model: posix
gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)
configure:2355: $? = 0
configure:2357: gcc -V </dev/null >&5
gcc: '-V' option must have argument
configure:2360: $? = 1
configure:2383: checking for C compiler default output file name
configure:2386: gcc    conftest.c  >&5
/usr/bin/ld: error while loading shared libraries: libbfd-2.16.91.0.5.so: cannot open shared object file: No such file or directory
collect2: ld returned 127 exit status
configure:2389: $? = 1

```

I checked that libbfd-2.16.91.0.5.so is missing. Instead there's an libbfd-2.16.91.so . I suppose I have an older version than gcc requests.
I made a hardlink to my file to avoid this problem, but now my computer complains that /usr/bin/ld requires version 'GLIBC_2.4' of /lib/tls/i686/cmov/libc.co.6.

Has anybody an idea/suggestion how to fix this? I suppose getting new versions of binutils and glibc would mess up quite a lot dependencies...

thx for your help!

---

### Post by ichigo on 2006-09-07
I just checked what happens if I run gcc in the terminal. Again it says:
```
/usr/bin/ld: error while loading shared libraries: libbfd-2.16.91.0.5.so: cannot open shared object file: No such file or directory
```
I think this means that I've got a problem with gcc, not Anjuta...:-? 
Any suggestions? Anybody?

---

### Post by ichigo on 2006-09-07
Managed to solve the problem myself!
My binutils were messed up, so I just reinstalled them.
As far as I can see, everything's working now.

---

