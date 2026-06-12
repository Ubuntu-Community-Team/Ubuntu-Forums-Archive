---
title: "Interesting error when using getaddrinfo(), please help"
date: 2008-12-22
forum: Programming Talk
---

### Post by Fallen_Demon on 2008-12-22
Hey, I'm a newbie to network programming (but not to C ;) )and have written a little C function to help me connect to a server on a known port. The problem is, when I try to call getaddrinfo I get a huge stack trace telling me I screwed up:
```
comp% ./app 
User's name is user
app folder is /home/user/.app
+---------------------------------------------------------+
|                       App                               |
|                  Shell Client                           |
+---------------------------------------------------------+
1. Connect to server
2. Exit
1
Please enter domain name:
localhost
Attempting to connect to localhost...
*** glibc detected *** ./app: free(): invalid next size (normal): 0x0804ac70 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb7e26a85]
/lib/tls/i686/cmov/libc.so.6(cfree+0x90)[0xb7e2a4f0]
/lib/tls/i686/cmov/libc.so.6(fclose+0x134)[0xb7e153e4]
/lib/tls/i686/cmov/libnss_files.so.2(_nss_files_gethostbyname2_r+0x14d)[0xb7f1a83d]
/lib/tls/i686/cmov/libc.so.6[0xb7e77398]
/lib/tls/i686/cmov/libc.so.6(getaddrinfo+0x199)[0xb7e78ad9]
./hm_client[0x8048794]
./hm_client[0x80489e7]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0)[0xb7dd1450]
./hm_client[0x80486b1]
======= Memory map: ========
08048000-08049000 r-xp 00000000 08:03 802398     /home/user/NetBeans/hivemind_server/app
08049000-0804a000 rw-p 00001000 08:03 802398     /home/user/NetBeans/hivemind_server/app
0804a000-0806b000 rw-p 0804a000 00:00 0          [heap]
b7c00000-b7c21000 rw-p b7c00000 00:00 0 
b7c21000-b7d00000 ---p b7c21000 00:00 0 
b7dba000-b7dbb000 rw-p b7dba000 00:00 0 
b7dbb000-b7f04000 r-xp 00000000 08:03 67152      /lib/tls/i686/cmov/libc-2.7.so
b7f04000-b7f05000 r--p 00149000 08:03 67152      /lib/tls/i686/cmov/libc-2.7.so
b7f05000-b7f07000 rw-p 0014a000 08:03 67152      /lib/tls/i686/cmov/libc-2.7.so
b7f07000-b7f0a000 rw-p b7f07000 00:00 0 
b7f0a000-b7f16000 r-xp 00000000 08:03 472604     /usr/local/lib/libgcc_s.so.1
b7f16000-b7f17000 rw-p 0000b000 08:03 472604     /usr/local/lib/libgcc_s.so.1
b7f17000-b7f20000 r-xp 00000000 08:03 67162      /lib/tls/i686/cmov/libnss_files-2.7.so
b7f20000-b7f22000 rw-p 00008000 08:03 67162      /lib/tls/i686/cmov/libnss_files-2.7.so
b7f22000-b7f26000 rw-p b7f22000 00:00 0 
b7f26000-b7f27000 r-xp b7f26000 00:00 0          [vdso]
b7f27000-b7f41000 r-xp 00000000 08:03 137658     /lib/ld-2.7.so
b7f41000-b7f43000 rw-p 00019000 08:03 137658     /lib/ld-2.7.so
bff45000-bff5a000 rw-p bffeb000 00:00 0          [stack]
zsh: abort      ./app

```
And yes, I do have a server I know works. Anyway, here is my C code (more or less a copy paste from a tutorial after my code threw the same thing):
```

/*
 *client.c - provides a level of abstraction for a client
 *@author Fallen_Demon 
 *@version v0.1
 *@date 22/12/2008
 */


#include<sys/socket.h>
#include<sys/types.h>
#include<netdb.h>
#include<string.h>
#include<netinet/in.h>
#include<sys/wait.h>
#include<signal.h>
#include<arpa/inet.h>
#include<unistd.h>
#include<errno.h>

#define PORT "4483"

int connect_to_serv(const char* serv){
    /*connect to hivemind server serv
     *@return socket file descriptor, -1 on an error
     */
    int status;
    struct addrinfo hints;
    struct addrinfo *servinfo;   // will point to the results

    memset(&hints, 0, sizeof hints); // make sure the struct is empty

    hints.ai_family = AF_UNSPEC;      // don't care IPv4 or IPv6
    hints.ai_socktype = SOCK_STREAM; // TCP stream sockets
    // get ready to connect
    status = getaddrinfo(serv, PORT, &hints, &servinfo); //Obscene comment removed. This is definitely the line causing it though
    // servinfo now points to a linked list of 1 or more struct addrinfos

    if(status != -1){
        connect(status, servinfo->ai_addr, servinfo->ai_addrlen);
    }

    freeaddrinfo(&hints);
    freeaddrinfo(servinfo);

    return status;
}

```
I think I stripped out all my obscene language from a couple of hours of frustrated hacking and documentation scouring, sorry in advance if I've left any in. Thanks for your help everyone :)

---

### Post by dwhitney67 on 2008-12-22
According to the API for getaddrinfo(), your call to that function looks fine.  What I would suspect that is/will cause a problem is this call:
```

freeaddrinfo(&hints);

```
The variable 'hints' is created on the stack, hence there is no need to free it.

Also, you should consider declaring PORT as follows:
```

const char* PORT = "4483";

```

Using #define does not provide a data type; maybe that could also be throwing getaddrinfo() for a spin.

Btw, for what it is worth, I never found a need to use getaddrinfo() in setting up a client.  Do you really need it, and if so, why?

---

### Post by Fallen_Demon on 2008-12-22
As I said, I'm a network programming newbie ;) I'm 99.9% sure that the call to getaddrinfo is the one crashing it, as I surrounded it with annoyed printf calls to figure out where it was aborting. I also thought that the macro PORT value would be an implicit string value as it is surrounded by quotes. How would you suggest I connect? getaddrinfo is the only way I've seen it done in my short time with the appropriate APIs :(

---

### Post by dwhitney67 on 2008-12-22
For starters, check you connect() call.  It appears that by mistake you are passing the status that is returned by the getaddrinfo() call.  You should be passing the socket descriptor that you obtained from a call to socket().

As far as how I did things, I chose to use C++; the syntax is similar to C, so bear with the following:

```

void
TCPClientSocket::Connect(const std::string& socketName)
{
  sockaddr_un serverAddr;

  memset(&serverAddr, 0, sizeof serverAddr);

  serverAddr.sun_family = m_Domain;
  strncpy(serverAddr.sun_path, socketName.c_str(), socketName.size());

  if (connect(m_Socket, (sockaddr*) &serverAddr, SUN_LEN(&serverAddr)) == -1)
  {
    throw std::runtime_error("Could not connect to give address!");
  }
}

```

And...
```

void
TCPClientSocket::Connect(const std::string& foreignAddress, unsigned short foreignPort)
{
  sockaddr_in destAddr;

  FillAddress(foreignAddress, foreignPort, destAddr);

  if (connect(m_Socket, (sockaddr*) &destAddr, sizeof(destAddr)) == -1)
  {
    throw std::runtime_error("Could not connect to give address/port!");
  }
}

```
FillAddress() is implemented as such:
```

void
Socket::FillAddress(const std::string& address, unsigned short port, sockaddr_in& addr)
{
  hostent* host = gethostbyname(address.c_str());

  if (host == 0)
  {
    throw std::runtime_error("Could not get hostname from given address!");
  }

  memset(&addr, 0, sizeof(addr));

  addr.sin_family      = m_Domain;
  addr.sin_addr.s_addr = *((unsigned long *) host->h_addr_list[0]);
  addr.sin_port        = htons(port);
}

```

I do not profess to be an expert with TCP nor UDP sockets.  But I have used them in the past on a couple of projects, and the knowledge I gained, incomplete as it may be, led me to develop a C++ library that encapsulates some of the common features needed to set up servers and clients.  The code above is part of this library.

---

### Post by Fallen_Demon on 2008-12-22
I'm from a very heavy Java background, so coming down this close to the hardware is new to me. I also chose C because I don't want to fall into the trap of using OOP in every single situation when there could be better alternatives, hence I'm trying to diversify a little ;) Thanks a heap for your help, I'll be getting right back into it :)

---

