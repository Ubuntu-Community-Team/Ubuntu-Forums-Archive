---
title: "connection refused in my client server program"
date: 2010-10-23
forum: Programming Talk
---

### Post by jamesbon on 2010-10-23
I wrote a simple client server socket program in C.
The program did worked I compiled 
```

cc server.c -o server.o
cc client.c -o client.o

```and executed
```

./server.o
./client.o
```Things were running successfully.
After this I disconnected and again tried to run the client program this time I got error
```

ooprs: client1: Connection refused

```here is the code server.c
```

#include <sys/types.h>
#include <sys/socket.h>
#include <stdio.h>
#include <netinet/in.h>
#include <arpa/inet.h>
#include <unistd.h>
int
main ()
{
  int server_sockfd, client_sockfd;
  int server_len, client_len;
  struct sockaddr_in server_address;
  struct sockaddr_in client_address;
  server_sockfd = socket (AF_INET, SOCK_STREAM, 0);
  server_address.sin_family = AF_INET;
  server_address.sin_addr.s_addr = inet_addr ("127.0.0.1");
  server_address.sin_port = 9734;
  server_len = sizeof (server_address);
  bind (server_sockfd, (struct sockaddr *) &server_address, server_len);
  listen (server_sockfd, 5);
  while (1)
    {
      char ch;
      printf ("server waiting\n");
      client_len = sizeof (client_address);
      client_sockfd =
        accept (server_sockfd, (struct sockaddr *) &client_address,
                &client_len);
      read (client_sockfd, &ch, 1);
      ch++;
      write (client_sockfd, &ch, 1);
      close (client_sockfd);
    }

}

```and client.c
```

#include <sys/types.h>
#include <sys/socket.h>
#include <stdio.h>
#include <netinet/in.h>
#include <arpa/inet.h>
#include <unistd.h>
#include <stdlib.h>
int
main ()
{
  int sockfd;
  int len;
  int result;
  struct sockaddr_in address;
  char ch = 'A';
  sockfd = socket (AF_INET, SOCK_STREAM, 0);
  address.sin_family = AF_INET;
  address.sin_addr.s_addr = inet_addr ("127.0.0.1");
  address.sin_port = 9734;
  len = sizeof (address);
  result = connect (sockfd, (struct sockaddr *) &address, len);
  if (result == -1)
    {
      perror ("ooprs: client1");
      exit (1);
    }
  write (sockfd, &ch, 1);
  read (sockfd, &ch, 1);
  printf ("char from server = %c\n", ch);
  close (sockfd);
  exit (0);
}


```

---

### Post by dwhitney67 on 2010-10-23
You set up the port incorrectly, in both the server and the client.

You need to pass the port number to htons().  For example:
```

server_address.sin_port = htons(9734);

```

P.S.  Also, fix the declaration of the parameter(s) to accept().  Use -Wall when you compile your source code.... and please, refer to the man-pages before using an unfamiliar function from the C library.

---

### Post by jamesbon on 2010-10-23
I am running this program on local machine 127.0.0.1 and as I mentioned it was executing also so why do I need to use htons here.
When I run this program 
./server.o and ./client.o every thing is going fine for some time.
I get following response
> char from server = B

When I do a Ctrl+C on server program 
and then again try to run

./server.o and ./client.o 
then I get ooprs: client1: Connection refused

---

### Post by dwhitney67 on 2010-10-23
1.  There's no need to bounce the server every time you want to run the client.

2.  When you do bounce the server, more than likely the bind() is **failing** because you are attempting to use a port that technically is still in "use".

3.  To mitigate item 2 above, a) check the returned result value from bind(), and b) consider setting up the socket option to "re-use" the port.  For example:
```

int yes = 1;
setsockoption(server_sockfd, SOL_SOCKET, SO_REUSEADDR, (void*) &yes, (socklen_t) sizeof(yes));

```

As for the use of the htons(), you do it because that is what the documentation says to do.  If you want a more detailed or better explanation, use Google.

---

### Post by jamesbon on 2010-10-23
You are right bind is returning -1 if interrupt and restart server.o I checked.
htons,atons I know have read in beejs network programming guide.
The book  I have will deal about setsockopt in coming sections. I am reading and understanding how to write client server programs.
Thanks for your help I was initially thinking my program is not able to maintain proper que of incoming connections.
Is there any command by which I can find out if a port is busy.

---

