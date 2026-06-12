---
title: "gcc4.6.3 compilation gives error: C Compiler cannot create executables"
date: 2014-03-11
forum: Packaging and Compiling Programs
---

### Post by Abhimanyu_Shegokar on 2014-03-11
I am trying to install gcc 4.6.3 from scratch with mpc, mpfr and gmp from their sources too.

i am getting the following error

configure: error: in `/home/abhimanyu/gcc/gccbuild/i686-pc-linux-gnu/libgomp':
configure: error: C compiler cannot create executables
See `config.log' for more details.
make[3]: *** [configure-stage1-target-libgomp] Error 77
make[2]: *** [stage1-bubble] Error 2
make[1]: *** [all] Error 2
make: *** [gccinstall] Error 2

here is my [config.log]("http://pastebin.com/AMM3AMTH") file

---

### Post by Abhimanyu_Shegokar on 2014-03-21
anybody here to help??

---

### Post by steeldriver on 2014-03-21
Is there a separate config.log inside the /home/abhimanyu/gcc/gccbuild/i686-pc-linux-gnu/libgomp directory? The one you have posted (from the top level ./configure) doesn't seem to contain anything relevant.

---

