---
title: "Tower of Hanoi, simple client server"
date: 2011-04-04
forum: Programming Talk
---

### Post by Haunter99 on 2011-04-04
Hello....
i'm actually new to this sort of programming using ubuntu....
i been assign with a simple c programming work, but kinda stuck right now...
the question is like this:
In this project, you are required to implement the Tower of Hanoi   program. 
The server should wait for connection from client, once connected, the   client will send the number of disk that the client want the server to   solve. The server will then print out the number of steps required to   solve the puzzle with the required number of disks.

Here is an example of the output:

Server: Waiting for connection
Server: Received connection from 192.168.1.111
Client: 6
Server: For 6 disks, the steps required are 24 ( Not the actual answer,  just a guess)
Client: 24 steps

so i have tried to use Stream server but the program is now fully error :(
so i hope someone can help me to make the server recieve the input from client and sent back a message with the answer... thanx in advance.

---

### Post by dwhitney67 on 2011-04-04
What programming language will you be using?

Also, be careful of the level of help you seek for your HOMEWORK problem.  This thread could be closed if it is deemed that you are looking for answers without actually doing any of the WORK yourself.

---

### Post by PaulM1985 on 2011-04-04
Have you got any example code so far?  Have you done any research?

Is this:
[http://www.silicontao.com/ProgrammingGuide/other/beejnet.pdf](http://www.silicontao.com/ProgrammingGuide/other/beejnet.pdf)
of any use?

Paul

---

### Post by Haunter99 on 2011-04-04
i'm using c language... i have the coding...

this is server side:
```

#include <stdio.h>
#include <stdlib.h>
#include <unistd.h>
#include <errno.h>
#include <string.h>
#include <sys/types.h>
#include <sys/socket.h>
#include <netinet/in.h>
#include <netdb.h>
#include <arpa/inet.h>
#include <sys/wait.h>
#include <signal.h>

#define PORT "3490" // the port users will be connecting to

#define BACKLOG 10 // how many pending connections queue will hold

void sigchld_handler(int s)
{
    while(waitpid(-1, NULL, WNOHANG) > 0);
}

// get sockaddr, IPv4 or IPv6:
void *get_in_addr(struct sockaddr *sa)
{
    if(sa->sa_family == AF_INET) {
        return &(((struct sockaddr_in*)sa)->sin_addr);
    }

    return &(((struct sockaddr_in6*)sa)->sin6_addr);
}

int main(int argc, char *argv[])
{
    char buffer[256];
    char buf[256];
    char buffer2[256];
    int sockfd, new_fd; // listen on sock_fd, new connection on new_fd
    struct addrinfo hints, *servinfo, *p;
    struct sockaddr_storage their_addr; // connector's address information
    socklen_t sin_size;
    struct sigaction sa;
    int yes=1, n, n2;
    char s[INET6_ADDRSTRLEN];
    int rv;
    double ans=0;

    memset(&hints, 0, sizeof hints);
    hints.ai_family = AF_UNSPEC;
    hints.ai_socktype = SOCK_STREAM;
    hints.ai_flags = AI_PASSIVE; // use my IP

    if((rv = getaddrinfo(NULL, PORT, &hints, &servinfo)) != 0) {
        fprintf(stderr, "getaddrinfo: %s\n", gai_strerror(rv));
        return 1;
    }

    // loop through all the results and bind to the first we can
    for(p = servinfo; p != NULL; p = p->ai_next) { 
        if((sockfd = socket(p->ai_family, p->ai_socktype, p->ai_protocol)) == -1) {
            perror("server: socket");
            continue;
    }

    if(setsockopt(sockfd, SOL_SOCKET, SO_REUSEADDR, &yes, sizeof(int)) == -1) {
        perror("setsockopt");
        exit(1);
    }

    if(bind(sockfd, p->ai_addr, p->ai_addrlen) == -1) {
        close(sockfd);
        perror("server: bind");
        continue;
    }

    break;
}

if(p == NULL) {
    fprintf(stderr, "server: failed to bind\n");
    return 2;
}

freeaddrinfo(servinfo); // all done with this structure

if(listen(sockfd, BACKLOG) == -1) {
    perror("listen");
    exit(1);
}

sa.sa_handler = sigchld_handler; // reap all dead processes
sigemptyset(&sa.sa_mask);
sa.sa_flags = SA_RESTART;
if(sigaction(SIGCHLD, &sa, NULL) == -1) {
    perror("sigaction");
    exit(1);
}

printf("server: waiting for connections...\n");

while(1) { // main accept() loop
    sin_size = sizeof their_addr;
    new_fd = accept(sockfd, (struct sockaddr *)&their_addr, &sin_size);
    if(new_fd == -1) {
        perror("accept");
        continue;
    }

    inet_ntop(their_addr.ss_family, get_in_addr((struct sockaddr *)&their_addr), s, sizeof s);
    printf("server: got connection from %s\n", s);
     
    bzero(buffer,256);
         n = read(new_fd,buffer,255);

         if (n < 0) error("ERROR reading from socket");
    ans = atof(buffer);
    ans = pow(2.0,ans)-1;
    //printf("server1: For %s disks the steps required are %lf\n",buffer, ans);
        *(double*)buf = ("server1: For %s disks the steps required are %lf\n",buffer, ans);
         n = write(new_fd,buf,255);
         if (n < 0) error("ERROR writing to socket");

    /*bzero(buffer2,256);
         n2 = read(new_fd,buffer2,255);
         if (n2 < 0) error("ERROR reading from socket");
        printf("server2: %s\n",buffer2);
         n2 = write(new_fd,buffer2,255);
         if (n2 < 0) error("ERROR writing to socket");*/

    return 0;
}
}

```

---

### Post by Haunter99 on 2011-04-04
this is client side:

```

#include <stdio.h>
#include <stdlib.h>
#include <unistd.h>
#include <errno.h>
#include <string.h>
#include <netdb.h>
#include <sys/types.h>
#include <netinet/in.h>
#include <sys/socket.h>

#include <arpa/inet.h>

#define PORT "3490" // the port client will be connecting to

#define MAXDATASIZE 100 // max number of bytes we can get at once

// get sockaddr, IPv4 or IPv6:
void *get_in_addr(struct sockaddr *sa)
{
    if(sa->sa_family == AF_INET) {
        return &(((struct sockaddr_in*)sa)->sin_addr);
    }

    return &(((struct sockaddr_in6*)sa)->sin6_addr);
}

int main(int argc, char *argv[])
{
    int sockfd, n, n2;

    struct addrinfo hints, *servinfo, *p;
    int rv;
    char s[INET6_ADDRSTRLEN];
char buffer[256];
char buffer2[256];

    if(argc != 2) {
       fprintf(stderr, "usage: client hostname\n");
       exit(1);
    }

    memset(&hints, 0, sizeof hints);
    hints.ai_family = AF_UNSPEC;
    hints.ai_socktype = SOCK_STREAM;

    if((rv = getaddrinfo(argv[1], PORT, &hints, &servinfo)) != 0) {
      fprintf(stderr, "getaddrinfo: %s\n", gai_strerror(rv));
      return 1;
    }

    // loop through all the results and connect to the first we can
    for(p = servinfo; p != NULL; p = p->ai_next) {
        if((sockfd = socket(p->ai_family, p->ai_socktype, p->ai_protocol)) == -1) {
        perror("client: socket");
        continue;
    }

    if(connect(sockfd, p->ai_addr, p->ai_addrlen) == -1) {
       close(sockfd);
       perror("client: connect");
       continue;
    }

    break;
    }

    if(p == NULL) {
    fprintf(stderr, "client: failed to connect\n");
    return 2;
    }

    inet_ntop(p->ai_family, get_in_addr((struct sockaddr *)p->ai_addr), s, sizeof s);

    printf("client1: ");
    bzero(buffer,256);
    fgets(buffer,255,stdin);
    n = write(sockfd,buffer,strlen(buffer));
    if (n < 0) 
         error("ERROR writing to socket");
    bzero(buffer,256);
    n = read(sockfd,buf,255);
    if (n < 0) 
         error("ERROR reading from socket");
    printf("server1: %s\n",buf);

  /*  printf("client2: ");
    bzero(buffer2,256);
    fgets(buffer2,255,stdin);
    n2 = write(sockfd,buffer2,strlen(buffer2));
    if (n2 < 0) 
         error("ERROR writing to socket");
    bzero(buffer2,256);
    n2 = read(sockfd,buffer2,255);
    if (n2 < 0) 
         error("ERROR reading from socket");
    printf("server2: %s\n",buffer2);*/

    return 0;
}

 
```

*the goal is i want the client to be able to print out the answer from the server....
i've been try searching for solution but none of it is compatible with my work....

---

### Post by dwhitney67 on 2011-04-04
Haunter, re-edit your posts and place your code within CODE blocks.  It makes it a lot easier to read.

---

### Post by dwhitney67 on 2011-04-04
Client is sending a newline along with the input; remove the newline before sending data:
```

fgets(buffer,255,stdin);
n = write(sockfd,buffer,strlen(buffer));

```

Server is doing something quite odd here:
```

*(double*)buf = ("server1: For %s disks the steps required are %lf\n",buffer, ans);

```
Perhaps you should consider using snprintf()?
```

snprintf(buf, sizeof(buf) - 1, "server1: For %s disks the steps required are %lf\n", buffer, ans);

```
Note, the 'buffer' will have a newline in it, unless you correct what the client is sending.

P.S.  bzero() was deprecated years ago; use memset() instead.

---

### Post by Haunter99 on 2011-04-04
Thanx, that solve the problem....

---

