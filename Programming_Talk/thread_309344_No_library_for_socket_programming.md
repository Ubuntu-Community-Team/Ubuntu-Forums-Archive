---
title: "No library for socket programming"
date: 2006-11-29
forum: Programming Talk
---

### Post by nignasi on 2006-11-29
Hi,

I'm trying to compile some C programs with TCP/UDP sockets on a new Kubuntu 6.10. In fat I have the same problem mentioned in this forum

[http://www.ubuntuforums.org/showthread.php?t=123645&highlight=-lsocket](http://www.ubuntuforums.org/showthread.php?t=123645&highlight=-lsocket)

This a fragment from makefile

------------------------------------
COMPILER = gcc
LIB = -lsocket -lnsl
OBJ = connectsock.o errexit.o 

TCPdaytime: connectTCP.o $(OBJ) TCPdaytime.c
	$(COMPILER) TCPdaytime.c connectTCP.o $(OBJ) -o TCPdaytime $(LIB)
------------------------------------

and this is 'make TCPdaytime' result.

---------------------------------
$ make TCPdaytime
gcc TCPdaytime.c connectTCP.o connectsock.o errexit.o  -o TCPdaytime -lsocket -lnsl
/usr/bin/ld: cannot find -lsocket
collect2: ld returned 1 exit status
make: *** [TCPdaytime] Error 1
-----------------------------------

I already tried to load happycoders-libsocket and changed -lsocket with libsocket without success.

What can I do?

Thanks,

Ignasi

---

### Post by hod139 on 2006-11-29
Try installing 
```

happycoders-libsocket-dev
``` but leave it as -lsocket

---

