---
title: "sockets in kubuntu: how to see them"
date: 2012-12-12
forum: Programming Talk
---

### Post by icegood on 2012-12-12
Hi there! I'm newbie in sockets programming nd tried to understand how they registered in system. Tried example 3.3 from [here]("http://alas.matf.bg.ac.rs/manuals/lspe/snode=35.html")
and found that at least under my system (kubuntu 12.10) program prints nothing. "List open files" doesn't print too. What changes since then?
And yeah, i've changed grep argument to righ one, namely a.out and even stop program under gdb onthat system call to find footprints of registered that way socket, but still nothing.
For your convience just duplicate code:
```

/* inetaddr.c:
 *
 * Example using inet_addr(3):
 */
#include <stdio.h>
#include <unistd.h>
#include <stdlib.h>
#include <errno.h>
#include <string.h>
#include <sys/types.h>
#include <sys/socket.h>
#include <netinet/in.h>
#include <arpa/inet.h>

/*
 * This function reports the error and
 * exits back to the shell:
 */
static void bail(const char *on_what) 
{
  
  fprintf(stderr, "%s: %s\n", on_what, strerror(errno));
  exit(1);
}

int main(int argc,char **argv)
{
  int z;
  struct sockaddr_in adr_inet;/* AF_INET */
  int len_inet;                /* length  */
  int sck_inet;                 /* Socket */
  /* Create a Socket */
  sck_inet = socket(AF_INET,SOCK_STREAM,0);
  if ( sck_inet == -1 )
    bail("socket()");
  /* Establish address */
  memset(&adr_inet,0,sizeof adr_inet);
  adr_inet.sin_family = AF_INET;
  adr_inet.sin_port = htons(9000);
  adr_inet.sin_addr.s_addr =inet_addr("127.0.0.95");
  if ( adr_inet.sin_addr.s_addr == INADDR_NONE )
    bail("bad address.");
  len_inet = sizeof adr_inet;
  /* Bind it to the socket */
  z = bind(sck_inet, (struct sockaddr *)&adr_inet, len_inet);
  if ( z == -1 )
    bail("bind()");
  /* Display our socket address */
  system("netstat -pa --tcp 2>/dev/null | grep a.out");
  return 0;
}

```

---

### Post by dwhitney67 on 2012-12-12
You are attempting to setup a TCP socket.

In case you are ever in a dark alley, held at knife-point... or just in a job interview... and someone asks you how to setup a server socket using TCP, recite the following steps:

1.  Create the socket
2.  Bind the socket
3.  Listen on the socket
4.  Accept connections on the socket.

For a client application:

1.  Create the socket
2.  Connect to the server.

If your attempt was to setup a server application, you missed step 3, and possibly step 4 too, before your attempt to use netstat.

P.S.  Take the system() call out of your code.  Use a separate terminal from where you are running your application to monitor whether the TCP port is open and listening for connections.

---

### Post by muteXe on 2012-12-12
> **dwhitney67 said:**
> 

In case you are ever in a dark alley, held at knife-point... or just in a job interview... 

..or any combination thereof of course.

---

