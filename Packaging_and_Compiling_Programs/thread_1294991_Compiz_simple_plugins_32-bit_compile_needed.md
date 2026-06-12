---
title: "Compiz simple plugins 32-bit compile needed"
date: 2009-10-18
forum: Packaging and Compiling Programs
---

### Post by nullmind on 2009-10-18
I've been working on a compiz fusion plugin. I've got a little explanation on what it's based on and a video in [this article]("http://santiance.com/2009/10/compiz-fusion-plugin-development/"). It basically "slides" windows in using the Minimize/Unminimize. I got the base code from forums.compiz-fusion.org.

How can I compile it as 32-bit on my 64-bit system? If you need the source simply:

bzr pull [http://santiance.com/bzr/compiz-fusion-plugins-simple](http://santiance.com/bzr/compiz-fusion-plugins-simple)

Cheers,
Kris

---

### Post by nullmind on 2009-10-20
There is an effort to document the Compiz API for 0.9, so this may help other future plugin developers and people documenting compiz:

[http://santiance.com/doc/compiz/](http://santiance.com/doc/compiz/)

Cheers,
Kris

---

### Post by Bachstelze on 2009-10-20
You can compile 32bit programs on a 64bit system by passing the -m32 flag to gcc:

```
firas@iori ~ % uname -a
Linux iori.fkraiem.org 2.6.30-1-amd64 #1 SMP Sat Aug 15 18:09:19 UTC 2009 x86_64 GNU/Linux
firas@iori ~ % cat test.c
#include <stdio.h>

int main(void)
{
        long a;
        printf("%d\n", sizeof(a));
        return 0;
}

firas@iori ~ % cc -o test test.c
firas@iori ~ % ./test && file test
8
test: ELF 64-bit LSB executable, x86-64, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.6.18, not stripped
firas@iori ~ % cc -m32 -o test test.c
firas@iori ~ % ./test && file test
4
test: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.6.18, not stripped

```

---

### Post by nullmind on 2009-10-23
Thanks,
I had tried this, but the problem was that I was trying to build a i686 deb on a 64-bit machine. Your example makes me think I was doing it correctly and maybe this is the problem:

checkinstall --arch=i686

?

---

### Post by Bachstelze on 2009-10-23
Sorry, can't help you with checkinstall, I don't use that to build my DEBs.

---

### Post by dinxter on 2009-10-23
Checkinstall is probably best thought of as a wrapper around 'make install' for apt (and other package managers). It watches what this would do then creates simple packages to allow easier installation, handy for moving things about between my computers I find. But it does not in any way mean that the source is 'debianised' and that a proper debian package can be built. 
Bearing that in mind, a lot of the options to checkinstall are so that you can override its own auto-guessed details for how to name the created package file, version, licence and that sort of stuff. Changing the checkinstall architecture doesnt change any of the actual build parameters, just the package name. For instance, you could run through checkinstall and change the architecture to 'zx81' or anything else, the source is compiles fine exactly as before, we just have a package named packagename-1.0-1_zx81.deb instead of  packagename-1.0-1_i386.deb

---

### Post by Bachstelze on 2009-10-24
... in other words, you will have to build your packages The Proper Way(TM) :p

[https://wiki.ubuntu.com/PackagingGuide/Complete](https://wiki.ubuntu.com/PackagingGuide/Complete)

---

