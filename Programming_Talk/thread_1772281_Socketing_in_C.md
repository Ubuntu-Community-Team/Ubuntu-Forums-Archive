---
title: "Socketing in C"
date: 2011-05-31
forum: Programming Talk
---

### Post by rshinde70 on 2011-05-31
Guys, I'm running Ubuntu 10.10.
I'm learning socket programming in C. I've written two simple codes.
A serve and a client.
I'm facing some problems to rum 'em. Please guys, guide me in this code as I'm tired searching the error from last 3 hours.
I want your help.

Server : 

```
#include <stdio.h>
#include <sys/socket.h>
#include <sys/types.h>
#include <netinet/in.h>

int main(int argc, char **argv) {

    
    int socketfd, portno, i, cli_len, n;
    struct sockaddr_in serv_addr, cli_addr;
    char buffer[256];

    if (argc < 1) {
        printf("Args!\n");
           return 2;    
    }
    socketfd = socket(AF_INET, SOCK_STREAM, 0);
    if (socketfd < 0) {
        printf("Socket Err\n");
        return 2;
    }
    portno = atoi(argv[1]);
    serv_addr.sin_family = AF_INET;
    serv_addr.sin_port = htons(portno);
    serv_addr.sin_addr.s_addr = INADDR_ANY;

    i = bind(socketfd, (struct sockaddr *)&serv_addr, sizeof(serv_addr));
    if( i<0 ) {
        perror("Error bind failed");
        return 2;
    }

    if(-1 == listen(socketfd, 10)) {
        perror("Error listen failed");
        return 2;
    }
    cli_len = sizeof(cli_addr);
    printf("before accept\n");
    int accept_fd = accept(socketfd, (struct sockaddr *)&cli_addr, &cli_len);
    if (accept_fd < 0) {
        perror("Accept Error");
        return 2;
    } 
    printf("connection Successful!\n");
    n = read(accept_fd,buffer,255);
    if(n<0) printf("Read Err\n");
    printf("Here is the message : %s\n",buffer);    
    close(accept_fd);
    close(socketfd);

    return 0;
}
```

And the client is here >>
```

#include <sys/socket.h>
#include <sys/types.h>
#include <netinet/in.h>
#include <string.h>
#include <stdio.h>
#include <netdb.h>

int main(int argc, char *argv[]) {
    
    struct sockaddr_in serv_addr;
    struct hostent *server;
    int portno, socketFD, n;
    char buffer[256];

    portno = atoi(argv[2]);
    socketFD = socket(AF_INET, SOCK_STREAM, 0);
    if (socketFD < 0) {
        perror("Socket Error!");
    }
    server = gethostbyname(argv[1]);
    if (server == NULL) {
        fprintf(stderr, " ERROR\n ");
        return 2;
    }
    memset((char *) &serv_addr, '0', sizeof(serv_addr));
    serv_addr.sin_family = AF_INET;
    bcopy((char *)&server->h_addr, (char *)&serv_addr.sin_addr.s_addr, server -> h_length);
    serv_addr.sin_port = htons(portno);

    printf("before connect\n");

    n = connect(socketFD, (struct sockaddr *) &serv_addr, sizeof(serv_addr));
    if (n<0)  {
        perror("Connect Error");
        return 2;
    } 
    printf("Connection Established\n");
    memset((char *)&buffer, '0', sizeof(buffer));
    printf("Enter your message!\n");
    fgets(buffer,255,stdin);
    n = write(socketFD, buffer, strlen(buffer));
    if (n < 0) printf("Write error!\n");
    close(socketFD);
    return 0;
}    
```


I hope you guys help me as soon as possible. :)

---

### Post by Zugzwang on 2011-05-31
> **rshinde70 said:**
> I'm facing some problems to rum 'em. 

Start by describing your problem. Does the code compile? How do you compile it? Does it run? How do you run it? What are the error messages/what is the undesired behaviour observed?

---

### Post by dwhitney67 on 2011-05-31
> **Zugzwang said:**
> Start by describing your problem. Does the code compile? How do you compile it? Does it run? How do you run it? What are the error messages/what is the undesired behaviour observed?

Exactly!

But here's my guess:
```

    ...
    n = read(accept_fd,buffer,255);
    if(n<0) printf("Read Err\n");
    printf("Here is the message : %s\n",buffer);   **<--- Buffer is not null-terminated**
    ...

```

Other items worth mentioning:

1.  gethostbyname() and bcopy() have been "deprecated"; use getaddrinfo() and memcpy() instead.

2.  It is common to use send() and recv() vs. write() and read().

3.  After the fgets() in the client code, there is no code that removes the newline (if any) from the buffer.

---

### Post by Petrolea on 2011-05-31
> **Zugzwang said:**
> Start by describing your problem. Does the code compile? How do you compile it? Does it run? How do you run it? What are the error messages/what is the undesired behaviour observed?

Yes, please post the error. I'm not on Linux machine atm so I can't run this.

---

