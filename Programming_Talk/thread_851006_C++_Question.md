---
title: "C++ Question"
date: 2008-07-06
forum: Programming Talk
---

### Post by perlsyntax on 2008-07-06
What thing can i do with C++?

---

### Post by wrtpeeps on 2008-07-06
You can do a LOT of "things".

:-D

---

### Post by LaRoza on 2008-07-06
> **perlsyntax said:**
> What thing can i do with C++?

By the sound of it, probably nothing.

How well do you know C++? You could ask a more specific question to get better answers.

---

### Post by perlsyntax on 2008-07-06
What headers in C++ do i need for raw sockets?

---

### Post by henchman on 2008-07-06
if i don't get you wrong..

network support is not defined in the c++ standard, so you have to use your os' header files.

a quick search returned this, looks n1
[http://sage.mc.yu.edu/kbeen/teaching/networking/resources/sockets.html](http://sage.mc.yu.edu/kbeen/teaching/networking/resources/sockets.html)

edit: as most os' network libraries are coded in c, you may write your own c++ wrappers

---

### Post by gnusci on 2008-07-06
Well there are plenty socket libraries out there, I am no expert but I have found few that can be interesting

[http://ubuntuforums.org/showthread.php?t=216863](http://ubuntuforums.org/showthread.php?t=216863)

Some libraries

[http://www.cs.wustl.edu/~schmidt/ACE.html](http://www.cs.wustl.edu/~schmidt/ACE.html)
[http://rudeserver.com/socket/index.html](http://rudeserver.com/socket/index.html)
[http://netclass.sourceforge.net/](http://netclass.sourceforge.net/)
[http://www.alhem.net/Sockets/index.html](http://www.alhem.net/Sockets/index.html)
[http://sourceforge.net/projects/cpp-sockets/](http://sourceforge.net/projects/cpp-sockets/)

read toturials is always a good practice, maybe you can write your own library

[http://www.alhem.net/Sockets/tutorial/](http://www.alhem.net/Sockets/tutorial/) 
[http://beej.us/guide/bgnet/](http://beej.us/guide/bgnet/)

---

### Post by nvteighen on 2008-07-06
> **gnusci said:**
> 
read toturials is always a good practice, maybe you can write your own library

Personally, I love writing libraries... It's really fun and makes you think in creating something useful and usuable for a potential user.

---

### Post by perlsyntax on 2008-07-06
i try to install rudesocket but i get this error.

perlsyntax@perlsyntax-desktop:~/rudesocket-1.2.0$ make check
/bin/bash ./libtool --tag=CXX --mode=link g++  -g -O2   -o librudesocket.la -rpath /usr/local/lib -version-info 1:2:0 rude_socketimpl.lo socket.lo socket_comm.lo socket_comm_normal.lo socket_comm_ssh.lo socket_connect.lo socket_connect_normal.lo socket_connect_proxy.lo socket_connect_socks4.lo socket_connect_socks5.lo socket_connect_tunnel.lo socket_tcpclient.lo -lssl 
g++ -shared -nostdlib /usr/lib/gcc/i486-linux-gnu/4.2.3/../../../../lib/crti.o /usr/lib/gcc/i486-linux-gnu/4.2.3/crtbeginS.o  .libs/rude_socketimpl.o .libs/socket.o .libs/socket_comm.o .libs/socket_comm_normal.o .libs/socket_comm_ssh.o .libs/socket_connect.o .libs/socket_connect_normal.o .libs/socket_connect_proxy.o .libs/socket_connect_socks4.o .libs/socket_connect_socks5.o .libs/socket_connect_tunnel.o .libs/socket_tcpclient.o  -lssl -L/usr/lib/gcc/i486-linux-gnu/4.2.3 -L/usr/lib/gcc/i486-linux-gnu/4.2.3/../../../../lib -L/lib/../lib -L/usr/lib/../lib -L/usr/lib/gcc/i486-linux-gnu/4.2.3/../../.. -lstdc++ -lm -lc -lgcc_s /usr/lib/gcc/i486-linux-gnu/4.2.3/crtendS.o /usr/lib/gcc/i486-linux-gnu/4.2.3/../../../../lib/crtn.o  -Wl,-soname -Wl,librudesocket.so.1 -o .libs/librudesocket.so.1.0.2
/usr/bin/ld: cannot find -lssl
collect2: ld returned 1 exit status
make: *** [librudesocket.la] Error 1

---

### Post by CptPicard on 2008-07-06
Apparently you don't have the ssl dev library installed.

You really need to get comfortable with the very basics first before tackling something like sockets.

---

### Post by perlsyntax on 2008-07-06
How do i find ssl dev with apt-get?

---

### Post by nvteighen on 2008-07-06
> **perlsyntax said:**
> How do i find ssl dev with apt-get?
It's the libssl-dev package, if I'm not wrong.

---

### Post by LaRoza on 2008-07-06
> **perlsyntax said:**
> How do i find ssl dev with apt-get?

```

apt-cache search ssl-dev

```

That is how you search. For more control, you can pipe it into grep.

---

### Post by WW on 2008-07-06
> **LaRoza said:**
> ```

apt-cache search ssl-dev

```

That is how you search. For more control, you can pipe it into grep.

For what it's worth, I also find the search feature at [packages.ubuntu.com](http://packages.ubuntu.com/) very useful.

---

### Post by LaRoza on 2008-07-07
> **WW said:**
> For what it's worth, I also find the search feature at [packages.ubuntu.com](http://packages.ubuntu.com/) very useful.

Too graphical. :-)

---

