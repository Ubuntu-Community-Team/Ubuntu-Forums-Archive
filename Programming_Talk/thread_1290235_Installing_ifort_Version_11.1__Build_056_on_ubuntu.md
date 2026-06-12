---
title: "Installing ifort Version: 11.1  Build: 056 on ubuntu/hardy"
date: 2009-10-13
forum: Programming Talk
---

### Post by thekronisk on 2009-10-13
Hi.

I unsucessfully tried to install ifort on my ubuntu/hardy. Went to the intel website, gave them my email, downloaded **Product for IA-32/Intel® 64 (File l_cprof_p_11.1.056.tgz) **and extracted the archive.

When I then try to sh install.sh from terminal I get this error: trap: 260: SIGTSTP: bad trap.

I don't know what to do to make this work.
I've already installed gfortran (from synaptic, piece of cake) and it works fine, but for the course I'm taking I was told by my professor that tiresome compiler issues could be avoided if I use ifort instead.

Thank you for reading, I'm looking forward to your reply.


Regards,

Thekronisk

---

### Post by Zugzwang on 2009-10-13
Looks like an internal error. The only thing I can tell you is that there are instructions on installing that compiler somewhere around on the web. However, I can only find a german one. Here's the link to an automatic translation. It does not seem to use "install.sh" and might therefore work:

[http://translate.google.com/translate?u=http%3A%2F%2Fwiki.ubuntuusers.de%2FIfort&sl=de&tl=en&hl=en&ie=UTF-8](http://translate.google.com/translate?u=http%3A%2F%2Fwiki.ubuntuusers.de%2FIfort&sl=de&tl=en&hl=en&ie=UTF-8)

---

### Post by hamazi on 2009-10-23
Greetings,

Try "sudo ./install.sh" instead of "sudo sh ./install.sh"

Thanks,

---

### Post by bancage on 2009-12-06
hello, i have a problem when use intel fortran compiler 11.1, when i typed "ifort  hello.f90", the error information is " error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory".
i tried to install libstdc++ by typing "sudo apt-get install compat-libstdc++" in the terminal, but it said it can't find compat-libstd. 
btw, i  use Ubuntu 8.04. is it because Ubuntu 8.04 can't use intel fortran 11.1 or something else, thank you...

---

### Post by Zugzwang on 2009-12-07
> **bancage said:**
> i tried to install libstdc++ by typing "sudo apt-get install compat-libstdc++" in the terminal, but it said it can't find compat-libstd. 
btw, i  use Ubuntu 8.04. is it because Ubuntu 8.04 can't use intel fortran 11.1 or something else, thank you...

See here:

[http://packages.ubuntu.com/search?searchon=contents&keywords=libstdc%2B%2B.so.5&mode=filename&suite=hardy&arch=any](http://packages.ubuntu.com/search?searchon=contents&keywords=libstdc%2B%2B.so.5&mode=filename&suite=hardy&arch=any)

---

