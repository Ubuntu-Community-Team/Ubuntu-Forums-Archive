---
title: "Daytime server errors"
date: 2010-11-11
forum: Programming Talk
---

### Post by Hannon565 on 2010-11-11
I am trying to program a daytimeserver that returns the time and date but also prints out the client address
heres the server code 

```

#include <stdio.h> 
#include "unp.h" 
#include <time.h> 
 
int 
main (int argc, char **argv) 
{ 
    int    listenfd, connfd; 
    struct sockaddr_in servaddr, cliaddr; 
    char    buff[MAXLINE]; 
    time_t    ticks; 
    socklen_t len;//new variable 
 
 
    listenfd = Socket(AF_INET, SOCK_STREAM, 0); 
 
    bzero(&servaddr, sizeof(servaddr)); 
    servaddr.sin_family    = AF_INET; 
    servaddr.sin_addr.s_addr = htonl(INADDR_ANY); 
    servaddr.sin_port    = htons(atoi(argv[1])); 
 
    Bind(listenfd, (SA *) &servaddr, sizeof(servaddr)); 
 
    Listen(listenfd, LISTENQ); 
 
    for( ; ; ) 
    { 
        connfd = Accept(listenfd, (SA *) &cliaddr, &len); 
        printf("connection from %s, port %d\n", inet_ntop(AF_NET, 
        &cliaddr.sin_addr, buff, sizeof(buff)), 
        ntohs(cliaddr.sin_port)): 
    ticks = time(NULL); 
    snprintf(buff, sizeof(buff), "%.24s\r\n", ctime(&ticks)); 
    Write(connfd, buff, strlen(buff)); 
 
        Close(connfd); 
    } 
}

```

and heres the code for the client
```

#include "unp.h"

int
main(int argc, char **argv)
{
    int sockfd, n, counter = 0;
    char    recvline[MAXLINE + 1];
    struct sockaddr_in    servaddr;

    if(argc != 3)
        err_quit("usage: a.out <IPaddress>");

    if((sockfd = socket(AF_INET, SOCK_STREAM, 0)) <0)
        err_sys("socket error");

    bzero(&servaddr, sizeof(servaddr));
    servaddr.sin_family = AF_INET;
    servaddr.sin_port =htons(atoi(argv[2]));
    if(inet_pton(AF_INET, argv[1], &servaddr.sin_addr) <= 0)
        err_quit("inet_pton error for %s", argv[1]);

    if(connect(sockfd, (SA *) &servaddr, sizeof(servaddr)) <0)
        err_sys("connect error");

    while( (n = read(sockfd, recvline, MAXLINE)) >0)
    {
        counter++;
        recvline[n] = 0;
        if(fputs(recvline, stdout) == EOF)
            err_sys("fputs error");
    }

    if( n < 0)
        err_sys("read error");

    printf("counter = %d\n", counter);
    exit(0);
}

```

Cheers for any help provided

---

### Post by interval1066 on 2010-11-11
Might want to describe what help you need.

---

### Post by Hannon565 on 2010-11-11
Oh yeah sorry 
I am getting this error message

daytimeservsh2.c: In function ‘main’:
daytimeservsh2.c:29: error: ‘AF_NET’ undeclared (first use in this function)
daytimeservsh2.c:29: error: (Each undeclared identifier is reported only once
daytimeservsh2.c:29: error: for each function it appears in.)

I know on line 31 there is a : instead of ;

---

### Post by dwhitney67 on 2010-11-11
AF_INET -- what you have is misspelled.

Also, you need to include <sys/socket.h> (unless it is already included in unp.h).

P.S.  bzero() was deprecated sometime during the last millennium.  And why are you using Socket(), Bind(), Listen(), Accept(), Write(), and Close()... these should be socket(), bind(), listen(), accept(), write(), and close(), respectively.  Actually, in lieu of write(), most network developers use send().

---

