---
title: "cant find the source code associated with sys/socket.h"
date: 2015-02-22
forum: New to Ubuntu
---

### Post by nadav4 on 2015-02-22
well there isnt much more to it, i tried locate socket.c and didnt find anything and /usr/src/linux-headers-3.8.0-29/net/ipv4 seems to be empty, and i'm out of ideas. does anyone know where can i find the source file?

---

### Post by Holger_Gehrke on 2015-02-23
Do you actually have the kernel sources installed ? They aren't by default, because the headers are sufficient if you only want to compile other programs that need to call the kernel. Try 'apt-cache policy linux-source' to find out whether or not they are installed. If they are installed, you could try searching the output of 'dpkg -L linux-source'

---

### Post by nadav4 on 2015-02-23
no it was not installed. thank you

---

