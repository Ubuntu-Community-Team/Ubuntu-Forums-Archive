---
title: "socket error(client)"
date: 2012-10-12
forum: Packaging and Compiling Programs
---

### Post by shoxsz on 2012-10-12
I'm trying to create a client socket to send a http request to a server, but an error is occurring in the function connect, in turn primeir returned this error: "connect: Socket operating on non-socket 'and' connect: no such file or directory 'I did not find anything wrong in my code so I went looking two examples of client sockets, and they tanbem returned this error.

my code is this:

```

#include <stdio.h>
#include <stdlib.h>
#include <string.h>

#include <netdb.h>
#include <sys/types.h>
#include <sys/socket.h>
#include <netinet/in.h>
#include <arpa/inet.h>

char erro[80];

int host_para_ip(const char* host, char* ip);

int main(int argc, char* argv[])
{

    int sock;
    struct sockaddr_in addr;

    int porta = 80;
    char ip[16];

    if(argc == 1)
    {
        printf("Argumentos inválidos.\n");
        exit(1);
    }

    if(host_para_ip(argv[1], ip) == 1)
    {
        printf("Endereço inválido.\n");
        return 1;
    }


    if((sock = socket(AF_INET, SOCK_STREAM, 0) < 0))
    {
        perror("socket");
        return -1;
    }

    addr.sin_family = AF_INET;
    addr.sin_port = htons(porta);
    addr.sin_addr.s_addr = inet_addr(ip);

    if(connect(sock, (struct sockaddr*)&addr, sizeof(addr)) < 0)
    {
        perror("connect");
        return -1;
    }

    printf("Conectado!\n");


    return 0;
}

int host_para_ip(const char* host, char* ip)
{
    struct hostent* h = gethostbyname(host);

    if(h == NULL)
    {
        return 1;
    }

    strcpy(ip, (char*)inet_ntoa(*((struct in_addr *)h->h_addr)));

    return 0;

}

```


if anyone knows what is causing the error I am grateful.

---

### Post by spjackson on 2012-10-13
> 
    if((sock = socket(AF_INET, SOCK_STREAM, 0) < 0)) 
A closing parenthesis is in the wrong place. It should be
```

    if((sock = socket(AF_INET, SOCK_STREAM, 0)) < 0) 

```I'd also make sure I initialised all the members of the structure before setting any members.
```

    memset(&addr, 0, sizeof addr);

```

---

