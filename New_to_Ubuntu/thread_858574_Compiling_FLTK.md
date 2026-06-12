---
title: "Compiling FLTK"
date: 2008-07-13
forum: New to Ubuntu
---

### Post by thePowerworks on 2008-07-13
I have a fresh installation of ubuntu 8.04 and i'm trying to install fltk from source.

I have extracted the .tar.gz into the Documents folder. I then cd into the directory and type ./configure and I get the following error.

checking for gcc... gcc
checking for C compiler default output file name... 
configure: error: C compiler cannot create executables
See `config.log' for more details.


when I look in the config.log file I see the follow:

gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)
configure:2382: $? = 0
configure:2389: gcc -V >&5
gcc: '-V' option must have argument
configure:2392: $? = 1
configure:2415: checking for C compiler default output file name
configure:2442: gcc    conftest.c  >&5
/usr/bin/ld: crt1.o: No such file: No such file or directory
collect2: ld returned 1 exit status
configure:2445: $? = 1
configure:2483: result: 
configure: failed program was:

followed by a lot of text that I didn't fully understand.

Any help?

Thanks!

---

### Post by braddcadd on 2008-07-14
Does this thread help?
[http://ubuntuforums.org/showthread.php?t=145610](http://ubuntuforums.org/showthread.php?t=145610)

---

