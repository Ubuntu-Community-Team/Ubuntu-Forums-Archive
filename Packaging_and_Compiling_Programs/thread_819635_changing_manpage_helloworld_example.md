---
title: "changing manpage helloworld example"
date: 2008-06-05
forum: Packaging and Compiling Programs
---

### Post by BackwardsDown on 2008-06-05
I've done the first bit of the PackagingGuide, just before they are explaining CDBS ([https://wiki.ubuntu.com/PackagingGuide/Complete](https://wiki.ubuntu.com/PackagingGuide/Complete)) I had a working .deb, great.

Now I want to edit the tekst in the manpage and create a new .deb with my changes. But whatever I do, after every "debuild", and after installing the new .deb the "man hello" is still the same, I dont get it.

```
niels@inoue:~/motu/hello/hello-2.1.1$ ls
ABOUT-NLS    config.guess   configure     INSTALL      man            stamp-h
aclocal.m4   config.h       configure.ac  install-sh   missing        stamp-h1
AUTHORS      config.h.in    contrib       intl         mkinstalldirs  tests
BUGS         config.log     COPYING       m4           NEWS           THANKS
build-stamp  config.rpath   debian        Makefile     po             TODO
ChangeLog    config.status  depcomp       Makefile.am  README
ChangeLog.O  config.sub     doc           Makefile.in  src
```
```
niels@inoue:~/motu/hello/hello-2.1.1$ cd man
niels@inoue:~/motu/hello/hello-2.1.1/man$ ls
ChangeLog  hello.1  help2man  Makefile  Makefile.am  Makefile.in
niels@inoue:~/motu/hello/hello-2.1.1/man$ 
```

I edited hello.1 but after a rebuild nothing is changed in the manpage..

---

### Post by BackwardsDown on 2008-06-06
The manpage was beïng created by help2man, and it get's it contents by calling "hello --help", so by editing src/hello.c I was able to edit the manpage.

---

