---
title: "error: dereferencing pointer to incomplete type"
date: 2010-04-07
forum: Programming Talk
---

### Post by Akalic on 2010-04-07
Hey, I've been trying to get a basic server/client program using sockets to work and when I attempt to set the serv_add.sin_addr.s_addr to h_addr from gethostbyname() I get that error. I've been searching around, found many different ways to set the value, but none of them work. I'm almost certain its a stupid error on my part, but I can't find it for the life of me. 

```

#include <sys/types.h>
#include <sys/socket.h>
#include <netinet/in.h>
#include "../lib/my.h"

void exit(int);
void bzero(char*, int);
void bcopy(void*, void*, size_t);

int main(int argc, char** argv)
{
    int sockfd, portnum, n, exit_key;
    struct hostent* server;
    struct sockaddr_in serv_addr;

    char buffer[256];

    exit_key = 1;

    if (argc < 3)
    {
        my_str("Not enough parameters!\n");
        exit(1);
    }

    portnum = my_atoi(argv[2]);

    if ((sockfd = socket(AF_INET, SOCK_STREAM, 0)) < 0)
    {
        my_str("Socket error!\n");
        exit(1);
    }

    if ((server = gethostbyname(argv[1])) == NULL)
    {
        my_str("No such host!\n");
        exit(1);
    }

    bzero((char*) &serv_addr, sizeof(serv_addr));
    serv_addr.sin_family = AF_INET;
    serv_addr.sin_port = htons(portnum);
    [b]
    //The four different ways I've tried to do this...

    //serv_addr.sin_addr.s_addr = (unsigned long*) server->h_addr;

    //bcopy(server->h_addr, (char*) &(serv_addr.sin_addr.s_addr), server->h_length);

    //inet_aton(server->h_addr, (struct in_addr*) &serv_addr.sin_addr.s_addr);

    //memcpy(&serv_addr.sin_addr.s_addr, server->h_addr, server->h_length);

    [/b]
    if (connect(sockfd, &serv_addr, sizeof(serv_addr)) < 0)
    {
        my_str("Error in connecting!\n");
        exit(1);
    }

    my_str("Enter nickname: ");
    n = read(0, buffer, 256);
    write(sockfd, buffer, n);



    while (exit_key)
    {
        buffer[0] = '\0';
        n = 0;
        my_str("Enter text: ");
        n = read(0, buffer, 256);
        write(sockfd, buffer, n);

        buffer[n] = '\0';

        if (my_strcmp(buffer, "!exit") == 0)
            exit_key = 0;
    }

    my_str("Good bye...\n");

}

```

---

### Post by heikaman on 2010-04-07
have you tried this:

[PHP]
serv_addr.sin_addr.s_addr = htonl(server->h_addr) ;
[/PHP]

---

### Post by pbrane on 2010-04-07
You might try **getaddrinfo** instead. My understanding is that **gethostbyname** is deprecated. Here is a function I wrote to resolve a hostname:
```

int resolveHost(char* host, struct sockaddr_in *sockaddr)
{
  struct addrinfo hints, *res;
  char addrstr[100];
  void *ptr = 0;

  memset(&hints, 0, sizeof (hints));
  hints.ai_family = PF_UNSPEC;
  hints.ai_socktype = SOCK_STREAM;
  hints.ai_flags |= AI_CANONNAME;

  int error = getaddrinfo(host, NULL, &hints, &res);
  switch (error) {
    default: // no error (error == 0)
      break;
    .
    .
    // all possible errors returned by getaddrinfo
    .
    .
    .
  }

  while (res) {
    inet_ntop (res->ai_family, res->ai_addr->sa_data, addrstr, 100);

    switch (res->ai_family) {
      case AF_INET:
        ptr = &((struct sockaddr_in *) res->ai_addr)->sin_addr;
        break;
      case AF_INET6:
        // we don't support IPV6 at this time, if we did...
        //ptr = &((struct sockaddr_in6 *) res->ai_addr)->sin6_addr;
        return 0;
    }
    inet_ntop (res->ai_family, ptr, addrstr, 100);
    memcpy(sockaddr.sin_addr, ptr, sizeof(struct in_addr));

    res = res->ai_next;
  }
  return 1;
}

```

This function was originally written in C++ and gtkmm, but I think I managed to make it C. But you get the idea.

---

### Post by Akalic on 2010-04-07
Just did, same errors.

---

### Post by gnometorule on 2010-04-07
That's a stack issue I'm sure; not which function you use. Sitting in a cafe and need to run; but note....

- server is a pointer only
- that pointer is set to a (temporary) location in your line '...gethostaddress'
- the location that pointer then points to will have been overwritten by the time you try to access where it points to.

Hence, no (more) complete type. This may be somewhat off, but play with actually copying the CONTENT of what you request as opposed to a POINTER TO THE CONTENT (as that content can and will change). 

Best of luck.

---

### Post by Akalic on 2010-04-07
So far, nothing is working, and I know that gethostbyname is obsolete, but it's required for what I'm doing.

---

### Post by gnometorule on 2010-04-09
You probably moved on, but here is what I think needs to be changed for this to run. I didn't compile it myself as I forgot all the server related commands you're using; this only corrects the poorly coded use of a pointer.

Old:
```

    struct hostent* server;
     
        --- other code here as before (?) --

    if ((server = gethostbyname(argv[1])) == NULL

```New:

```

      (erase top definition)    

       -- other code as before (?) ---

    struct hostent server = *gethostbyname(argv[1]);
    struct hostent* server_p = &server; 

    if (server_p == NULL)

      -- etc, now use hostent_p (or hostent) as needed --

```I say "other code as before (?)" as there might be other errors; this just corrects your use of a pointer.

Here is another attempt to explain the pointer issue. In a line such as

```

    if ((server = gethostbyname(argv[1])) == NULL

```, the compiler does the following:

```

struct* temp_variable = gethostbyname(argv[1]);
server = temp_variable.

```The information you need is stored in some temporary variable. I forgot how this is usally implemented, but I would assume either on the stack or in the free store. So at the moment of assignment, your pointer 'server' points to the correct information. However, nothing prevents the compiler from erasing/freeing up/overwriting temp_variable with other information. When you then next use 'server', it still points to the same memory address, but the information stored there does not have to be the same anymore - it could be: if you try another compiler, this might work.

But as it only MIGHT work, never just assign a pointer to something that is not stored for the lifetime of the scope you need it in.

I added a simple example to show how we are really talking about a different object here:

```

#include <stdio.h>

int main()
{
        struct test{
                int a;
                int b;
        };
        struct test filler = { 2, 3};
        struct test* filled_p = &filler;
        printf("%s%p%s", "Pointer first points here: ", filled_p, "\n");

        struct test filled = *filled_p;
        filled_p = &filled;
        printf("%s%p%s", "Pointer now points here: ", filled_p,"\n");

        printf("%s%d %d %p\n", "original structure: ",
                filler.a, filler.b, &filler);
        printf("%s%d %d %p\n", "printed from copy of structure: ",
                filled.a, filled.b, &filled);
        printf("%s %d %d %p\n","printed from copy of structure via a pointer: ",
                filled_p->a, filled_p->b, &filled_p);
}

```prints out

```

Pointer first points here: 0xbfaf74c4
Pointer now points here: 0xbfaf74bc
original structure: 2 3 0xbfaf74c4
printed from copy of structure: 2 3 0xbfaf74bc
printed from copy of structure via a pointer:  2 3 0xbfaf74cc

```

---

### Post by Akalic on 2010-04-11
Fixed it, was missing an include.

```
#include <netdb.h>
```

Lesson today kids, REMEMBER TO CHECK YOUR INCLUDES.

---

### Post by sujithmo on 2011-10-21
I have the same problem with a code....

here is the code ... the error shown is dereferencing pointer to incompatible types...

#include<stdio.h>
#include<string.h>
#include<sys/types.h>
#include<sys/socket.h>
#include<netinet/in.h>
#include<netdb.h>

#define PORTNUM 8080
#define oops(msg) { perror(msg);exit(1);}

void main(int ac, char **av)
{
struct sockaddr_in saddr;
struct hostnet *hp;
char hostname[256];
int slen,sock_id,sock_fd;
FILE *sock_fp;
char *ctime();
long time(), thetime;
gethostname(hostname,256);
hp=gethostbyname(hostname);
bzero(&saddr,sizeof(saddr));
**bcopy(hp->h_addr,&(saddr.sin_addr),hp->h_length);**
saddr.sin_family=AF_INET;
saddr.sin_port=htons(8080);
sock_id=socket(AF_INET,SOCK_STREAM,0);
if(sock_id==-1)
oops("socket");
if(bind(sock_id,&saddr,sizeof(saddr))!=0)

while(1)
{
sock_fd=accept(sock_id,NULL,NULL);
printf("**Server: A new client connected!");
if(sock_fd==-1)
oops("accept");
sock_fp=fdopen(sock_fd,"w");

if(sock_fp==NULL)
oops("fdopen");

thetime=time(NULL);

fprint(sock_fp,"**************************\n");
fprintf(sock_fp,"**From server: the current is :");
fprintf(sock_fp,"%s",ctime(&thetime));
fprintf(sock_fp,"**************************\n");
fclose(sock_fp);
fflush(stdout);
}
}

pls help me to resolve it.... im a beginner in c programming...

---

### Post by Arndt on 2011-10-22
> **sujithmo said:**
> I have the same problem with a code....

here is the code ... the error shown is dereferencing pointer to incompatible types...

#include<stdio.h>
#include<string.h>
#include<sys/types.h>
#include<sys/socket.h>
#include<netinet/in.h>
#include<netdb.h>

#define PORTNUM 8080
#define oops(msg) { perror(msg);exit(1);}

void main(int ac, char **av)
{
struct sockaddr_in saddr;
struct hostnet *hp;
char hostname[256];
int slen,sock_id,sock_fd;
FILE *sock_fp;
char *ctime();
long time(), thetime;
gethostname(hostname,256);
hp=gethostbyname(hostname);
bzero(&saddr,sizeof(saddr));
**bcopy(hp->h_addr,&(saddr.sin_addr),hp->h_length);**
saddr.sin_family=AF_INET;
saddr.sin_port=htons(8080);
sock_id=socket(AF_INET,SOCK_STREAM,0);
if(sock_id==-1)
oops("socket");
if(bind(sock_id,&saddr,sizeof(saddr))!=0)

while(1)
{
sock_fd=accept(sock_id,NULL,NULL);
printf("**Server: A new client connected!");
if(sock_fd==-1)
oops("accept");
sock_fp=fdopen(sock_fd,"w");

if(sock_fp==NULL)
oops("fdopen");

thetime=time(NULL);

fprint(sock_fp,"**************************\n");
fprintf(sock_fp,"**From server: the current is :");
fprintf(sock_fp,"%s",ctime(&thetime));
fprintf(sock_fp,"**************************\n");
fclose(sock_fp);
fflush(stdout);
}
}

pls help me to resolve it.... im a beginner in c programming...

Your "hostnet" is a misspelling, it should be "hostent".

---

