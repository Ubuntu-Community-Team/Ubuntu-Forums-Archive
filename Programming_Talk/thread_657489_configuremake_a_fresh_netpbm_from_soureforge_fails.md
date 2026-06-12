---
title: "configure/make a fresh netpbm from soureforge fails"
date: 2008-01-03
forum: Programming Talk
---

### Post by bsenftner on 2008-01-03
All,

After realizing that 'apt-get install netpbm' installs a package with some of the netpbm utilities missing (at least pamscale and pamcomp) I went to sourceForge and downloaded the tarball of the entire thing.
After some additional apt-get'ing for things that the configure script complained about my system missing, I run 'make' and get this error:

[INDENT]
/usr/bin/ld: libpm.o: relocation R_X86_64_32 against `a local symbol' can not be used when making a shared object; recompile with -fPIC
libpm.o: could not read symbols: Bad value
collect2: ld returned 1 exit status
make[1]: *** [libnetpbm.so.10.26] Error 1
[/INDENT]


This exhausts my configure/make skills... I'm an old dinosaur that still writes my makefiles by hand (been coding since the 70's)...
Which makefile would I go about adding this "-fPIC" to?

Has anyone else needed these programs? I'm surprised that I can't find any mention that they are missing from the package...

---

### Post by alvarojunio on 2008-07-02
Hi,

I'm new here. This is my first post. 
I have the same problem whith you. Do you solve your problem? If "yes", can you say what do you do?
Thanks.

Álvaro Junio.

---

