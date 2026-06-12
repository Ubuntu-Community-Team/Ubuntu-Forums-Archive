---
title: "Odd error at the end of the program. A crash perhaps?"
date: 2009-03-22
forum: Programming Talk
---

### Post by YourSurrogateGod on 2009-03-22
Here is my code. There is a tar file if you want to download it.

coordinator.c
```
// server.c:

#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <sys/types.h> 
#include <sys/socket.h>
#include <netinet/in.h>
#include <netdb.h>

int dostuff(int socket, int TheValue);

void error(char * msg);

int main(int argc, char ** argv)
{
	int TheValue = 0;

  struct sockaddr_in serv_addr;
  struct sockaddr_in cli_addr;

  if(argc < 2)
  {
    fprintf(stderr,"ERROR, no port provided\n");
    exit(1);
  }

  int sockfd = socket(AF_INET, SOCK_STREAM, 0);

  if(sockfd < 0)
  {
    error("ERROR opening socket");
  }

  memset((char * ) &serv_addr, 0, sizeof(serv_addr));
  int portno = atoi(argv[1]);
  serv_addr.sin_family = AF_INET;
  serv_addr.sin_addr.s_addr = INADDR_ANY;
  serv_addr.sin_port = htons(portno);

  if(bind(sockfd, (struct sockaddr *) &serv_addr, sizeof(serv_addr)) < 0) 
  {
    error("ERROR on binding");
  }

  listen(sockfd,5);
  int clilen = sizeof(cli_addr);

  while(1)
  {
    int newsockfd = accept(sockfd, (struct sockaddr *) &cli_addr, &clilen);

    if(newsockfd < 0) 
    {
      error("ERROR on accept");
    }

    TheValue = dostuff(newsockfd, TheValue);
    close(newsockfd);
  } /* end of while */

	return 0;
}

int dostuff(int sock, int TheValue)
{
  int n = 0;
  char buffer[256];
  char valstr[256];

  memset(buffer, 0, 256);
  memset(valstr, 0, 256);

	sprintf(valstr, "%d", TheValue);
	n = write(sock, valstr, 256);

  if(n < 0)
  {
    error("ERROR reading from socket");
  }

  n = read(sock, buffer, 255);
  TheValue = atoi(buffer);

  if(n < 0)
  {
    error("ERROR writing to socket");
  }

	return TheValue;
}

void error(char * msg)
{
    perror(msg);
    exit(1);
}

```

server.c
```
// server.c:

#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <sys/types.h> 
#include <sys/socket.h>
#include <netinet/in.h>
#include <netdb.h>

void dostuff(int socket, char * coordHost, int coordPort);
void error(char * msg);
int connectToCoordinator(int increment, char * coordHost, int coordPort);

int main(int argc, char ** argv)
{
  struct sockaddr_in serv_addr;
  struct sockaddr_in cli_addr;

  if(argc < 4)
  {
    fprintf(stderr, "ERROR, no port provided\n");
    fprintf(stderr, "Use: <app> <app port> <coord host> <coord port>\n\n");
    exit(1);
  }

	char * coordinatorHost = argv[2];
	int coordinatorPort = atoi(argv[3]);

  int sockfd = socket(AF_INET, SOCK_STREAM, 0);

  if(sockfd < 0)
  {
    error("ERROR opening socket");
  }

  memset((char * ) &serv_addr, 0, sizeof(serv_addr));
  int portno = atoi(argv[1]);
  serv_addr.sin_family = AF_INET;
  serv_addr.sin_addr.s_addr = INADDR_ANY;
  serv_addr.sin_port = htons(portno);

  if(bind(sockfd, (struct sockaddr *) &serv_addr, sizeof(serv_addr)) < 0) 
  {
    error("ERROR on binding");
  }

  listen(sockfd, 5);
  int clilen = sizeof(cli_addr);

  while(1)
  {
    int newsockfd = accept(sockfd, (struct sockaddr *) &cli_addr, &clilen);

    if(newsockfd < 0) 
    {
      error("ERROR on accept");
    }

    dostuff(newsockfd, coordinatorHost, coordinatorPort);
    close(newsockfd);
  }

	// we should never get to this point.
  return 0;
}

void dostuff(int sock, char * coordHost, int coordPort)
{
  char buffer[256];

  memset(buffer, 0, 256);
  int n = read(sock, buffer, 255);
  int increment = atoi(buffer);

  if(n < 0)
  {
    error("ERROR reading from socket");
  }

  int newVal = connectToCoordinator(increment, coordHost, coordPort);

	sprintf(buffer, "%d", newVal);

  //sprintf(valstr, "you said: %s ", buffer);
  n = write(sock, buffer, 256);
  if(n < 0)
  {
    error("ERROR writing to socket");
  }
}

int connectToCoordinator(int change, char * coordHost, int coordPort)
{
  struct sockaddr_in serv_addr;
  struct hostent *server;

  char receiveBuffer[256];
	char sendBuffer[256];

	if((coordPort < 2001) && (coordPort > 65000))
  {
    fprintf(stderr, "the coordinator port that you gave is too small/large, please try again.");
    exit(1);
  }

  int sockfd = socket(AF_INET, SOCK_STREAM, 0);

  if(sockfd < 0)
  {
    error("ERROR opening socket");
  }

  server = gethostbyname(coordHost);

  if(server == NULL)
  {
    fprintf(stderr, "ERROR, no such host\n");
    exit(0);
  }

  memset((char * ) &serv_addr, 0, sizeof(struct sockaddr_in));
  serv_addr.sin_family = AF_INET;
  bcopy((char * )server->h_addr, 
    (char * )&serv_addr.sin_addr.s_addr, 
    server->h_length);
  serv_addr.sin_port = htons(coordPort);

  if(connect(sockfd, &serv_addr, sizeof(struct sockaddr_in)) < 0)
  {
    error("ERROR connecting");
  }

  memset(receiveBuffer, 0, 256);
  int n = read(sockfd, receiveBuffer, 255);

  if(n < 0)
  {
    error("ERROR reading from socket");
  }

	int amount = atoi(receiveBuffer);

	amount = amount + change;
	
	sprintf(sendBuffer, "%d", amount);

	n = write(sockfd, sendBuffer, strlen(sendBuffer));

	if(n < 0)
  {
    error("ERROR writing to socket");
  }

	return amount;
}

void error(char * msg)
{
    perror(msg);
    exit(1);
}

```

client.c
```
// client.c:

#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <sys/types.h>
#include <sys/socket.h>
#include <netinet/in.h>
#include <netdb.h> 

void error(char * msg);

int main(int argc, char ** argv)
{
  struct sockaddr_in serv_addr;
  struct hostent *server;

  char receiveBuffer[256];
	char sendBuffer[11];

  if(argc < 3)
  {
    fprintf(stderr, "usage %s hostname port\n", argv[0]);
    exit(1);
  }

  unsigned int portno = atoi(argv[2]);

  if((portno < 2001) && (portno > 65000))
  {
    fprintf(stderr, 
      "the port that you gave is too small/large, please try again.");
    exit(1);
  }

  printf("blah1\n\n");

  int sockfd = socket(AF_INET, SOCK_STREAM, 0);

  if(sockfd < 0)
  {
    error("ERROR opening socket");
  }

  server = gethostbyname(argv[1]);

  printf("blah2\n\n");

  if(server == NULL)
  {
    fprintf(stderr,"ERROR, no such host\n");
    exit(0);
  }

  memset((char * ) &serv_addr, 0, sizeof(serv_addr));
  serv_addr.sin_family = AF_INET;
  bcopy((char * )server->h_addr, (char * )&serv_addr.sin_addr.s_addr, 
    server->h_length);
  serv_addr.sin_port = htons(portno);

  printf("blah4\n\n");

  if(connect(sockfd, &serv_addr, sizeof(struct sockaddr_in)) < 0)
  {
    error("ERROR connecting");
  }

  printf("blah3\n\n");

  printf("Please enter the amount by which you would like to change the global value: ");
  memset(sendBuffer, 0, 256);
  scanf("%10s", &sendBuffer);

  printf("blah5\n\n");

  int n = write(sockfd, sendBuffer, strlen(sendBuffer));

  printf("blah6\n\n");

  if(n < 0)
  {
    error("ERROR writing to socket");
  }

  printf("blah7\n\n");

  memset(receiveBuffer, 0, 256);
  n = read(sockfd, receiveBuffer, 255);

  printf("blah8\n\n");

  if (n < 0)
  {
    error("ERROR reading from socket");
  }

  printf("blah9\n\n");

  printf("%s\n", receiveBuffer);

  printf("al;sdkjf\n\n");

  return 0;
}

void error(char * msg)
{
  perror(msg);
  exit(1);
}

```

Makefile:
```
# Makefile

all:coordinator server client

coordinator: coordinator.o 
	gcc coordinator.o -o coordinator -lnsl
coordinator.o: coordinator.c
	gcc -c coordinator.c

server: server.o
	gcc server.o -o server -lnsl
server.o: server.c
	gcc -c server.c

client: client.o
	gcc client.o -o client -lnsl
client.o: client.c
	gcc -c client.c

clean:
	rm *.o client server coordinator

```

Here is what happens when I run it.
```
$ ./client ysger 23234
blah1

blah2

blah4

blah3

Please enter the amount by which you would like to change the global value: 22
blah5

blah6

blah7

blah8

blah9

58
al;sdkjf

*** stack smashing detected ***: <unknown> terminated
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(__fortify_fail+0x48)[0xb7ecd138]
/lib/tls/i686/cmov/libc.so.6(__fortify_fail+0x0)[0xb7ecd0f0]
[0x8048b08]
[0x0]
======= Memory map: ========
08048000-08049000 r-xp 00000000 08:03 5079312    /home/ysg/Desktop/MyDocuments/Classes/URI/CSC512/ProgrammingAssignments/Assignment1/WithCoordinator/client
08049000-0804a000 rw-p 00000000 08:03 5079312    /home/ysg/Desktop/MyDocuments/Classes/URI/CSC512/ProgrammingAssignments/Assignment1/WithCoordinator/client
0804a000-0806b000 rw-p 0804a000 00:00 0          [heap]
b7dbd000-b7dc7000 r-xp 00000000 08:03 4349971    /lib/libgcc_s.so.1
b7dc7000-b7dc8000 rw-p 0000a000 08:03 4349971    /lib/libgcc_s.so.1
b7ddf000-b7de0000 rw-p b7ddf000 00:00 0 
b7de0000-b7f29000 r-xp 00000000 08:03 4367603    /lib/tls/i686/cmov/libc-2.7.so
b7f29000-b7f2a000 r--p 00149000 08:03 4367603    /lib/tls/i686/cmov/libc-2.7.so
b7f2a000-b7f2c000 rw-p 0014a000 08:03 4367603    /lib/tls/i686/cmov/libc-2.7.so
b7f2c000-b7f2f000 rw-p b7f2c000 00:00 0 
b7f2f000-b7f43000 r-xp 00000000 08:03 4367609    /lib/tls/i686/cmov/libnsl-2.7.so
b7f43000-b7f45000 rw-p 00013000 08:03 4367609    /lib/tls/i686/cmov/libnsl-2.7.so
b7f45000-b7f47000 rw-p b7f45000 00:00 0 
b7f51000-b7f52000 rw-p b7f51000 00:00 0 
b7f52000-b7f5b000 r-xp 00000000 08:03 4367612    /lib/tls/i686/cmov/libnss_files-2.7.so
b7f5b000-b7f5d000 rw-p 00008000 08:03 4367612    /lib/tls/i686/cmov/libnss_files-2.7.so
b7f5d000-b7f60000 rw-p b7f5d000 00:00 0 
b7f60000-b7f61000 r-xp b7f60000 00:00 0          [vdso]
b7f61000-b7f7b000 r-xp 00000000 08:03 4350645    /lib/ld-2.7.so
b7f7b000-b7f7d000 rw-p 00019000 08:03 4350645    /lib/ld-2.7.so
bf8c4000-bf8d9000 rw-p bffeb000 00:00 0          [stack]
Aborted

```

Why is it crashing like that? I don't understand. It seems to be doing the right thing with the incrementing and such. My C is rusty as an old steam locomotive in an age of diesels and electrics.

Furthermore, when I compile my app, I get this.
```
$ make
gcc -c coordinator.c
gcc coordinator.o -o coordinator -lnsl
gcc -c server.c
server.c: In function ‘connectToCoordinator’:
server.c:130: warning: passing argument 2 of ‘connect’ from incompatible pointer type
gcc server.o -o server -lnsl
gcc -c client.c
client.c: In function ‘main’:
client.c:64: warning: passing argument 2 of ‘connect’ from incompatible pointer type
gcc client.o -o client -lnsl
```

Why are those warnings there? I don't get it.

What other types of pointers can I possibly stuff in there?

Any help is appreciated.

---

### Post by dwhitney67 on 2009-03-22
Look at what you are doing here!

```

  char sendBuffer[11];
...
  memset(sendBuffer, 0, 256);
  scanf("%10s", &sendBuffer);

```
You are indeed smashing the stack here; you also do not require to provide the address of sendBuffer in the scanf(), but I suppose that is ok.  But to be safe, you should be using fgets(), not scanf().

P.S.  Your connect() call should look similar to the following, although I believe the sizeof() is acceptable in lieu of SUN_LEN.
```

connect(sockfd, (struct sockaddr*) &serv_addr, SUN_LEN(&serv_addr));

```

---

### Post by YourSurrogateGod on 2009-03-22
> **dwhitney67 said:**
> Look at what you are doing here!

```

  char sendBuffer[11];
...
  memset(sendBuffer, 0, 256);
  scanf("%10s", &sendBuffer);

```
You are indeed smashing the stack here;
Gah! You're right! Whoops!
> **dwhitney67 said:**
> you also do not require to provide the address of sendBuffer in the scanf(), but I suppose that is ok.  But to be safe, you should be using fgets(), not scanf().
What's the difference/advantage?
> **dwhitney67 said:**
> P.S.  Your connect() call should look similar to the following, although I believe the sizeof() is acceptable in lieu of SUN_LEN.
```

connect(sockfd, (struct sockaddr*) &serv_addr, SUN_LEN(&serv_addr));

```
What's SUN_LEN?

Man, I've been missing out on the latest developments while in C# land :) .

---

### Post by dwhitney67 on 2009-03-22
> **YourSurrogateGod said:**
> 
What's the difference/advantage?

With fgets(), you can specify the length of the buffer where the data will be stored; with scanf(), you have no such ability.  This feature is helpful in preventing buffer overruns with malicious user input.

> **YourSurrogateGod said:**
> 
What's SUN_LEN?

It's a macro that is defined in /usr/include/sys/un.h.  I believe that in lieu of it, you can use a sizeof(struct sockaddr).

---

### Post by YourSurrogateGod on 2009-03-22
> **dwhitney67 said:**
> With fgets(), you can specify the length of the buffer where the data will be stored; with scanf(), you have no such ability.  This feature is helpful in preventing buffer overruns with malicious user input.

I dunno...
```
scanf("%10s", &sendBuffer);
```

I've tested that in another application and that will get me only 10 chars.

However, it does seem that with fgets it's easier to dynamically specify the number of chars. With scanf you'll have to do some messy string manipulation as opposed to setting just a simple integer. Makes it very simple :) .
> **dwhitney67 said:**
> It's a macro that is defined in /usr/include/sys/un.h.  I believe that in lieu of it, you can use a sizeof(struct sockaddr).
Yes, I have that file with SUN_LEN. Should I be using it over sizeof? What's the advantage?

---

### Post by dwhitney67 on 2009-03-22
> **YourSurrogateGod said:**
> ...
With scanf you'll have to do some messy string manipulation as opposed to setting just a simple integer. Makes it very simple :) .

Bingo!

> **YourSurrogateGod said:**
> 
Yes, I have that file with SUN_LEN. Should I be using it over sizeof? What's the advantage?
Beats me what the advantage is.  I just do what I read in books and/or tutorials.

---

### Post by YourSurrogateGod on 2009-03-23
Alright, thanks dude. If I have other issues, I'll bring them up.

---

### Post by YourSurrogateGod on 2009-03-23
I take that back.

Now that I think about it, I forgot to test the client app.

```
// client.c:

#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <sys/types.h>
#include <sys/socket.h>
#include <netinet/in.h>
#include <netdb.h>
#include <unistd.h>
#include <arpa/inet.h>

void error(char * msg);

int main(int argc, char ** argv)
{
  struct sockaddr_in serv_addr;
  struct hostent *server;

  char receiveBuffer[256];
	char sendBuffer[11];

  if(argc < 3)
  {
    fprintf(stderr, "usage %s hostname port\n", argv[0]);
    exit(1);
  }

  unsigned int portno = atoi(argv[2]);

  if((portno < 2001) && (portno > 65000))
  {
    fprintf(stderr, 
      "the port that you gave is too small/large, please try again.");
    exit(1);
  }

  printf("blah1\n\n");

  int sockfd = socket(AF_INET, SOCK_STREAM, 0);

  if(sockfd < 0)
  {
    error("ERROR opening socket");
  }

  server = gethostbyname(argv[1]);

  printf("blah2\n\n");

  if(server == NULL)
  {
    fprintf(stderr,"ERROR, no such host\n");
    exit(0);
  }

  memset((char * ) &serv_addr, 0, sizeof(struct sockaddr_in));
  serv_addr.sin_family = AF_INET;
  bcopy((char * )server->h_addr, (char * )&serv_addr.sin_addr.s_addr, 
    server->h_length);
  serv_addr.sin_port = htons(portno);

  printf("blah4\n\n");

  if(connect(sockfd, (struct sockaddr * )&serv_addr, 
    sizeof(struct sockaddr_in)) < 0)
  {
    error("ERROR connecting");
  }

  printf("blah3\n\n");

  printf("Please enter the amount by which you would like to change the global value: ");
  memset(sendBuffer, 0, 11);
  scanf("%10s", sendBuffer);

  printf("blah5\n\n");

  int n = write(sockfd, sendBuffer, strlen(sendBuffer));

  printf("blah6\n\n");

  if(n < 0)
  {
    error("ERROR writing to socket");
  }

  printf("blah7\n\n");

  memset(receiveBuffer, 0, 256);
  n = read(sockfd, receiveBuffer, 255);

  printf("blah8\n\n");

  if (n < 0)
  {
    error("ERROR reading from socket");
  }

  printf("blah9\n\n");

  printf("%s\n", receiveBuffer);

  printf("al;sdkjf\n\n");

  return 0;
}

void error(char * msg)
{
  perror(msg);
  exit(1);
}
```

I still get that ugly error about smashing the stack.

---

### Post by dwhitney67 on 2009-03-24
I tested your client application; it appears to be operating just fine when I provide it expected data.  For example, "localhost" for the server hostname, 9000 for the port, etc.  The scanf() is working as well, truncating the data to 10 bytes.

Anyhow, I would suggest that when calling memset(), memcpy(), or any other function that requires you to manipulate a buffer, to be careful.

In lieu of this:
```

memset(receiveBuffer, 0, 256);

```
try to get into the habit of either one of the following:
```

memset(receiveBuffer, 0, sizeof(receiveBuffer));

/* or, when you declare receiveBuffer */

char receiveBuffer[256] = {0};

```

The same concept applies when calling recv().  When calling send() with a string, use strlen() to obtain the number of bytes being sent, or when dealing with unformatted data, then rely on the size of the buffer.

P.S.  bcopy() is obsolete; use memcpy() instead.

---

