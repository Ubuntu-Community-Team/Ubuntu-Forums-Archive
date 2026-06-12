---
title: "C++ TCP Code not executing in the right order"
date: 2015-05-30
forum: Programming Talk
---

### Post by RaJiska on 2015-05-30
Hello, 

I've a little problem with my C++ program. Basically, here is a client version, it should listen to what servers sends, however, messages are displayed only when server closes the connection, and a printf("Something") I put at the top isn't triggered.
Here is the code:

```
#include <stdio.h>
#include <stdlib.h>
#include <unistd.h>
#include <string.h>
#include <sys/types.h>
#include <sys/socket.h>
#include <netinet/in.h>
#include <netdb.h>

void error(const char *msg)
{
    perror(msg);
    exit(0);
}

int main(int argc, char *argv[])
{
  printf("A1");
  int sockfd, portno, n;
  struct sockaddr_in serv_addr;
  struct hostent *server;

  char buffer[256];
  if (argc < 3) {
    fprintf(stderr,"usage %s hostname port\n", argv[0]);
    exit(0);
  }
  portno = atoi(argv[2]);
  sockfd = socket(AF_INET, SOCK_STREAM, 0);
  if (sockfd < 0) error("ERROR opening socket");
  server = gethostbyname(argv[1]);
  if (server == NULL) {
    fprintf(stderr,"ERROR, no such host\n");
    exit(0);
  }
  bzero((char *) &serv_addr, sizeof(serv_addr));
  serv_addr.sin_family = AF_INET;
  bcopy((char *)server->h_addr, (char *)&serv_addr.sin_addr.s_addr, server->h_length);
  serv_addr.sin_port = htons(portno);
  if (connect(sockfd, (struct sockaddr *) &serv_addr, sizeof(serv_addr)) < 0) error("ERROR connecting");

  for (;;)
  {
    bzero(buffer,256);
    n = read(sockfd,buffer,255);
    if (n < 0) error("ERROR reading from socket");
    buffer[n - 1] = 0;
    if (strlen(buffer) == 0)
    {
      printf("Client disconnected. Exitting.\n");
      break;
    }
    printf("MSG:%s",buffer);
  }
  close(sockfd);
  return 0;
}
```

When executed, for example, the first line of the main (printf("A1");) won't be triggered before I do a CTRL + C from the server version.
What is sent from the server is correctly sent since after sending several things, and making server losse connection, client simply goes in the loop and display all at once what server has sent.

Thanks for your help !

---

### Post by ofnuts on 2015-06-01
Most likely just a buffering problem... By default the output to TTY (consoles....) is line-buffered (output only happens when there is a "\n" in the stream) and output to everything else (files/pipes) is size-buffered (buffer size is 4K I think). So either [change the buffering mode of your streams](http://man7.org/linux/man-pages/man3/setbuf.3.html) or flush them after writing.

---

### Post by dwhitney67 on 2015-06-04
> **RaJiska said:**
> Hello, 

I've a little problem with my C++ program. 
...

Your code is actually written in C, which is not the same as C++.

As offnuts indicated, you should print a newline character when you use printf(), or use fflush(stdio) as an alternative.

There are other issues within your program which could lead to 'disasters' in a more complex program; for example if recv() should return 0, your program takes no specific action, but assumes it is safe to assign a zero to a negative offset from the beginning of buffer.

Also, there are cases when recv() returns a -1 result that are not fatal conditions.  You should check the errno value for either EAGAIN and/or EINTR before assuming that you must exit the program with an error.

---

