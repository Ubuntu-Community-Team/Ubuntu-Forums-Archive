---
title: "g++: trouble finding sockets and openssl libraries"
date: 2008-09-04
forum: Programming Talk
---

### Post by sandman887 on 2008-09-04
Hi, 

I just installed openssl and the sockets libraries found here:

openssl:
[http://www.openssl.org/](http://www.openssl.org/)

Sockets:
[http://www.alhem.net/Sockets/index.html](http://www.alhem.net/Sockets/index.html)

On the downloads page for the sockets, I noticed a link for libuuid, but it looks like it's for ext2; I have ext3. 

Anyway, I have downloaded his first sample .cpp program for sockets and tried compiling it with all sorts of combinations for the paths to the libraries and include directories of openssl and sockets, to no avail.

I have tried g++ -o displaysockets DisplaySocket.cpp -L/usr/local/include/Sockets -L/usr/local/ssl/include/openssl -lpthread

g++ -o displaysockets DisplaySocket.cpp -lSocket opensslhere... -lpthread

I have tried: g++ -o displaysockets DisplaySocket.cpp -I/usr/local/include -I/usr/local/ssl/include -lpthread and many other combinations. I have tried what he said on this page to compile it: 
[http://www.alhem.net/Sockets/tutorial/install.html](http://www.alhem.net/Sockets/tutorial/install.html)

Any ideas? Here are the errors I keep getting:

```
s$ g++ -o displaysocket DisplaySocket.cpp -L/usr/local/include/Sockets -L/usr/local/ssl/include/openssl -lpthread
In file included from DisplaySocket.cpp:26:
DisplaySocket.h:23:23: error: TcpSocket.h: No such file or directory
DisplaySocket.h:24:28: error: ISocketHandler.h: No such file or directory
DisplaySocket.h:27: error: expected class-name before ‘{’ token
DisplaySocket.h:29: error: expected `)' before ‘&’ token
DisplaySocket.cpp:33: error: expected `)' before ‘&’ token
DisplaySocket.cpp: In member function ‘void DisplaySocket::OnRead()’:
DisplaySocket.cpp:41: error: ‘TcpSocket’ has not been declared
DisplaySocket.cpp:43: error: ‘ibuf’ was not declared in this scope
DisplaySocket.cpp:46: error: ‘TCP_BUFSIZE_READ’ was not declared in this scope
DisplaySocket.cpp:47: error: ‘tmp’ was not declared in this scope
```

Thanks

---

### Post by Zugzwang on 2008-09-04
There exists a rule of thumb: Whenever there is a Ubuntu package for some library/software/whatever, install that and don't do it manually unless you have a very good reason. So please install openssl using Synaptic (don't forget the "-dev" package you need for development).

As far as Sockets goes, you said that you installed that. The question is: *how* did you do that? Did you "make" it and used "make install" as root? 

Oh, by the way, if you want to specify the include path, use -I for g++ insted of -L, so
```

g++ -o displaysockets DisplaySocket.cpp -L/usr/local/include/Sockets -L/usr/local/ssl/include/openssl -lpthread

```
is wrong. There should never be a path to an "include" directory after "-L", so it should be:
```

g++ -o displaysockets DisplaySocket.cpp -I/usr/local/include/Sockets -I/usr/local/ssl/include/openssl -lpthread

```

And then add "-lSockets" for linking against the socket library and find out the name for the openssl library yourself.

---

