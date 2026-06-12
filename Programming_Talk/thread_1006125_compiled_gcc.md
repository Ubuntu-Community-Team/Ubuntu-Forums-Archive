---
title: "compiled gcc"
date: 2008-12-09
forum: Programming Talk
---

### Post by nitro_n2o on 2008-12-09
Hi, does anybody knw where can i find a compiled gcc binary that works for i386? compiled in the sense that it has the dependencies and I just need to ./gcc and it works? 

thanks a lot

---

### Post by Sorivenul on 2008-12-09
> **nitro_n2o said:**
> Hi, does anybody knw where can i find a compiled gcc binary that works for i386? compiled in the sense that it has the dependencies and I just need to ./gcc and it works? 

thanks a lot

GCC is in the repositories; install "build-essential" and you should have it.

No need to include the "./" either, a simple:
```
gcc example.c -o example
```
should work.

---

### Post by nitro_n2o on 2008-12-09
thanks for the reply.. i knw that ubuntu is in the repo, but I have to use another machine - red hat - and I don't have any privileges what so ever. The gcc compiled rpm packages that I've found are not relocatable and I can't get them installed locally. Further, they keep complaining about unmet dependencies, which I can't find their binaries neither.. 

I also do not have enough disk quota to get gcc form source and compile! 

Yes, a horrible situation.. how can i live without GCC!!

I was wondering if someone knows a place where i can download a fully built gcc binary that will work without a problem

---

### Post by mali2297 on 2008-12-09
If you lack disk space, perhaps [tcc](http://bellard.org/tcc/) is a better option.

If you have access to an optical disk drive, then another alternative might be to use a Live CD like [KNOPPIX](http://www.knoppix.org/). As far as I know, it includes development tools.

---

### Post by PmDematagoda on 2008-12-09
> **nitro_n2o said:**
> thanks for the reply.. i knw that ubuntu is in the repo, but I have to use another machine - red hat - and I don't have any privileges what so ever. The gcc compiled rpm packages that I've found are not relocatable and I can't get them installed locally. Further, they keep complaining about unmet dependencies, which I can't find their binaries neither.. 

I also do not have enough disk quota to get gcc form source and compile! 

Yes, a horrible situation.. how can i live without GCC!!

I was wondering if someone knows a place where i can download a fully built gcc binary that will work without a problem

What version of Red Hat is it? Is it the old Red Hat or Red Hat Enterprise Linux?

---

### Post by nitro_n2o on 2008-12-09
I think it is a Fedora Core something.. 

tcc will not work, I need GCC, actually i'm trying to compile a matlab mex file and I need gcc 4+

thanks

---

### Post by mmix on 2008-12-10
[http://www.scratchbox.org/](http://www.scratchbox.org/) 

[http://www.scratchbox.org/download/files/sbox-releases/stable/tarball/scratchbox-toolchain-host-gcc-1.0.9-i386.tar.gz](http://www.scratchbox.org/download/files/sbox-releases/stable/tarball/scratchbox-toolchain-host-gcc-1.0.9-i386.tar.gz)

[http://wiki.openembedded.net/index.php/Main_Page](http://wiki.openembedded.net/index.php/Main_Page)

[http://thewrittenword.com/](http://thewrittenword.com/)

[http://www.openpkg.org/](http://www.openpkg.org/)

HTH

---

### Post by Cracauer on 2008-12-10
Why not compile it yourself?

---

### Post by iponeverything on 2008-12-10
> **Cracauer said:**
> Why not compile it yourself?

if you compile your program as a static binary, you won't have to worry about lib versions on the host machine.

---

### Post by Cracauer on 2008-12-11
I always compile new gccs into /opt/cvsversions or /opt/whatever.

I've been doing it for years and I don't recall that I ever had a problem when the main OS got upgraded.  The compiler isn't using any of that GNOME or KDE nonsense. Although glibc can a version mess, I haven't seen it affect anything non-graphical I drag around in /opt/*.

Trying to compile is into static binaries might be challenging.

---

