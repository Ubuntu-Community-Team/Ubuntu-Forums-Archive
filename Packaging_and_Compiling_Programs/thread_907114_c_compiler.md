---
title: "c compiler"
date: 2008-09-01
forum: Packaging and Compiling Programs
---

### Post by robsie on 2008-09-01
in a terminal i enter the ./configure command and i get this error 

 error: C compiler cannot create executables

i tried to install the "build essential" package and i get this 

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-libc-dev_2.6.24-19.36_i386.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-libc-dev_2.6.24-19.36_i386.deb)
  404 Not Found

any ideas ? thanks

---

### Post by modmadmike on 2008-09-01
try this link [http://gb.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-libc-dev_2.6.27-2.3_i386.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-libc-dev_2.6.27-2.3_i386.deb)
oh and try "apt-get install build-essential" from the terminal.

---

### Post by robsie on 2008-09-01
ive done that and it allowed me to install the build essential package but now i get a different error message :(

configure: error: No curses header-files found

---

### Post by modmadmike on 2008-09-01
Search synaptic for linux-headers and install the one for generic kernal (or whatever kernel your using)

---

### Post by modmadmike on 2008-09-01
wait nvm do you have libncurses5
to install it do a "sudo apt-get install libncurses5"

---

### Post by snova on 2008-09-01
libncurses5 isn't what you want, you need libncurses5-dev more than likely. It might be named something else, but look for the -dev suffix anyway.

Of course, you'll end up installing libncurses5 anyway...

The aforementioned package, by the way, only contains the libraries. The headers are in the package ending in -dev.

---

