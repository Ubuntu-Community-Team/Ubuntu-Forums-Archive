---
title: "C Networking"
date: 2009-06-13
forum: Programming Talk
---

### Post by Woody1987 on 2009-06-13
Im writing a program which at some stage will need to connect to a server and then download a file. Im at a loss as to how to implement this as i have never done any programming that involves networking. Basically i will have two functions, connectToServer() and downloadFromServer(). I assume that i will need to open up a socket which is what i want the connectToServer() function to do, and then to use that socket to download what i want using downloadFromServer(). Right now i dont have access to this server so the file i want to download is stored locally at 127.0.0.1/home/matt. What i have so far:

> #include <sys/types.h>
#include <sys/socket.h>

void connectToServer()
{
    char *serverAddress = "127.0.0.1/home/matt/";
}

void downloadFromServer()
{
}

As you can see i have pretty much nothing, but im hoping that someone here can help me.

---

### Post by dwhitney67 on 2009-06-13
If only it were that easy....


You may want to peruse [Beej's Guide to Network Programming]("http://beej.us/guide/bgnet/") for details/examples.

---

### Post by jimi_hendrix on 2009-06-13
beej's guide is probably the best, but this one is quick and dirty to set up sockets
[http://www.linuxhowtos.org/C_C++/socket.htm](http://www.linuxhowtos.org/C_C++/socket.htm)

---

### Post by Woody1987 on 2009-06-13
Using libcurl i have been able to create an ftp client.

---

### Post by soltanis on 2009-06-13
Yeah, libcurl was probably a good call. No point in re-inventing wheels.

---

