---
title: "Real VNC server installation problem"
date: 2008-06-21
forum: New to Ubuntu
---

### Post by fparodi on 2008-06-21
I downloaded the vnc-4_1_2-x86_linux.tar.gz file on my Ubuntu 8.04 PC and executed the vncinstall script, but when then I run the vncserver or vscpasswd programs I get an error about a library file they can't be found.
The file is libstdc++-libc6.2-2.so.3. I have in /usr/lib the following:
 /usr/lib/libstdc++.so.6.0.9

I tried to create a symb link to bypass the problem by it didn't work:
lrwxrwxrwx 1 root root      18 2008-06-19 22:33 /usr/lib/libstdc++-libc6.2-2.so.3 -> libstdc++.so.6.0.9

I also tried to add /usr/lib to the PATH, but it didn't help either.

Any suggestion?
Tx in advance.
Fabio

fabio@fabio-desktop:~$ vncpasswd
vncpasswd: error while loading shared libraries: libstdc++-libc6.2-2.so.3: cannot open shared object file: No such file or directory

---

### Post by Xerp on 2008-06-21
Try NoMachine. Works like VNC but much easier to get running:

[http://www.nomachine.com/](http://www.nomachine.com/)

Or, enable desktop sharing.

---

### Post by fparodi on 2008-06-21
Thanks for the hint.
I tried that one and works fine between Fedora6 -> Ubuntu 8.04, but not viceversa. I installed the SW on both but when I tried to connect from Ubuntu to Fedora6 the connection times out (Signal 15).

By the way I'd prefer to use VNC as the final goal is to use a Nokia N810 tablet as a VNC client to remotely monitor my Linux machines. On N810 only VNC is available to my knowledge.
Tx
Fabio:)

---

### Post by akhem on 2008-09-12
that lib is located inside of libstdc++2.10-glibc2.2

so do:

sudo apt-get install libstdc++2.10-glibc2.2

---

### Post by cariboo on 2008-09-12
Vnc4server is available in the repositories, there is no need to compile it. In a terminal type:

```
sudo apt-get install vnc4server
```

xvnc4viewer is also available.

Jim

---

