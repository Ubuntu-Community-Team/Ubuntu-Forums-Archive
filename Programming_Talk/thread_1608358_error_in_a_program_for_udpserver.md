---
title: "error in a program for udpserver"
date: 2010-10-28
forum: Programming Talk
---

### Post by jamesbon on 2010-10-28
```
#include<sys/types.h>
#include<sys/socket.h>
#include<stdio.h>
#include<netinet/in.h>
#include<arpa/inet.h>
#include<unistd.h>
#include<stdlib.h>
#define REQUEST 10
#define REPLY 10
int main(int argc,char *argv[]){
struct sockaddr_in serv;
char request[REQUEST],reply[REPLY];
int sockfd,n;
if(argc!=2)
 err_quit("usage: udpcli <IP add of server>");
if((sockfd =socket(PF_INET,SOCK_DGRAM,0))<0)
 err_sys("socket error");
  memset(&serv,0,sizeof(serv));
 serv.sin_family = AF_INET;
 serv.sin_addr.s_addr = inet_addr(argv[1]);
 serv.sin_port = htons(UDP_SERV_PORT);
 if(sendto(sockfd,request,REQUEST,0,(SA),&serv,sizeof(serv))!=REQUEST)
  err_sys("sendto error");
 if((n=recvfrom(sockfd,reply,REPLY,0,(SA)NULL,(int *)NULL))<0)
 err_sys("recvfrom error");
exit(0);
}

```Above is a code for UDP server which I am trying.
When I compile it I get following errors
```
udpserver.c: In function &#8216;main&#8217;:
udpserver.c:18: warning: incompatible implicit declaration of built-in function &#8216;memset&#8217;
udpserver.c:21: error: &#8216;UDP_SERV_PORT&#8217; undeclared (first use in this function)
udpserver.c:21: error: (Each undeclared identifier is reported only once
udpserver.c:21: error: for each function it appears in.)
udpserver.c:22: error: &#8216;SA&#8217; undeclared (first use in this function)
udpserver.c:22: warning: passing argument 6 of &#8216;sendto&#8217; makes integer from pointer without a cast
/usr/include/sys/socket.h:155: note: expected &#8216;socklen_t&#8217; but argument is of type &#8216;struct sockaddr_in *&#8217;
udpserver.c:22: error: too many arguments to function &#8216;sendto&#8217;

```Any suggestions.

---

### Post by johnl on 2010-10-29
```

#include <sys/types.h>
#include <sys/socket.h>
#include <stdio.h>
#include <netinet/in.h>
#include <arpa/inet.h>
#include <unistd.h>
#include <stdlib.h>
#include <memory.h> /* you need to include memory.h to fix the warning
                       about memset() */

#define REQUEST 10
#define REPLY 10

#define UDP_SERV_PORT 1600 /* this was not defined in your code ... but you used it.
                              so define it as whatever port you want. */

int main(int argc, char *argv[])
{
    struct sockaddr_in serv;

    char request[REQUEST];
    char reply[REPLY];
    
    int sockfd, n;

    if(argc != 2) {
        printf("usage: %s <ip address>\n", argv[0]);
        return 0;
    }
    
    if((sockfd = socket(PF_INET,SOCK_DGRAM,0)) < 0) {
        perror("socket:");
        return 0;
    }
    
    memset(&serv, 0 , sizeof(serv));
    
    serv.sin_family = AF_INET;
    serv.sin_addr.s_addr = inet_addr(argv[1]);
    serv.sin_port = htons(UDP_SERV_PORT);

    /* your (SA) was undefined and also an extra uneccesary argument. 
       also, you need to cast (&serv) to a (struct sockaddr*) */
    if (sendto(sockfd, request, REQUEST, 0, (struct sockaddr*)&serv,
              sizeof(serv)) != REQUEST) {
        perror("sendto:");
        return 0;
    }
    
    /* same issue here with (SA), also no need to cast NULL to an (int*) */
    if((n = recvfrom(sockfd, reply, REPLY, 0 , NULL, NULL)) < 0 ) {
        perror("recvfrom:");
    }
    
    return 0;
}

```

---

### Post by jamesbon on 2010-10-29
Thanks a lot for pointing these errors.

---

### Post by spjackson on 2010-10-29
> **johnl said:**
> ```

#include <memory.h> /* you need to include memory.h to fix the warning
                       about memset() */

```
I think it would usually be better to #include <string.h> rather than <memory.h> since:
a) There is no memory.h in the ISO C standard, and the standard tells you that memset is in string.h.
and b) "man memset" tells you that you need string.h

It works with <memory.h> because this in turn includes <string.h>

---

