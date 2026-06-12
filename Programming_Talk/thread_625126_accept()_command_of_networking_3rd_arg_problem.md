---
title: "accept() command of networking 3rd arg problem"
date: 2007-11-27
forum: Programming Talk
---

### Post by belikewater on 2007-11-27
Hello All,
I have started to study linux api networking,using a code for a server
I tryed to run it on linux ubuntu, kde/c++:


[COLOR="Blue"]struct sockaddr_in serv_addr, cli_addr;
sockfd = socket(AF_INET,SOCK_STREAM,0);
clilen = sizeof(cli_addr);
newsockfd = accept(sockfd, (struct sockaddr *) &cli_addr, &clilen);[/COLOR]

has a problem at 3rd argumnet custing:

tryed to follow the [COLOR="DarkOrchid"]Beej's Guide to Network Programming [/COLOR]
and wrote:

[COLOR="Blue"]
clilen = sizeof(struct sockaddr_in);

newsockfd = accept(sockfd, (struct sockaddr *) &cli_addr, &clilen);[/COLOR]
man pages also doesn't help 
so how can i solve the problem?:confused:

---

### Post by meatpan on 2007-11-28
> **belikewater said:**
> Hello All,

[COLOR="Blue"]struct sockaddr_in serv_addr, cli_addr;
sockfd = socket(AF_INET,SOCK_STREAM,0);
clilen = sizeof(cli_addr);
newsockfd = accept(sockfd, (struct sockaddr *) &cli_addr, &clilen);[/COLOR]



Where is clilen declared?  Is it of type 'socklen_t *'?  Also, can you post the compiler error output?

---

### Post by dwhitney67 on 2007-11-28
```
ACCEPT(2)                  Linux Programmer’s Manual                 ACCEPT(2)

NAME
       accept - accept a connection on a socket

SYNOPSIS
       #include <sys/types.h>          /* See NOTES */
       #include <sys/socket.h>

       int accept(int sockfd, struct sockaddr *addr, socklen_t *addrlen);
...

```


Usage:

```
int sockfd = -1;
int connection_fd = -1;
struct sockaddr addr;
socklen_t addrlen = 0;

sockfd        = socket( some_Domain, some_Type, some_Protocol );
connection_fd = accept( sockfd, &addr, &addrlen );
```

If you are not interested in the client address information, you can call accept() like this:

```
connection_fd = accept( sockfd, 0, 0 );
```

---

