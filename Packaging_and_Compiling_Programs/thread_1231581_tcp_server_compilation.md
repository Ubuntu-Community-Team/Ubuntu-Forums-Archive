---
title: "tcp server compilation"
date: 2009-08-04
forum: Packaging and Compiling Programs
---

### Post by joker31174 on 2009-08-04
When I try to compile a TCP server i get this:
----
main.cpp: In function ‘int main(int, char**)’:
main.cpp:40: error: invalid conversion from ‘int*’ to ‘socklen_t*’
main.cpp:40: error:   initializing argument 3 of ‘int accept(int, sockaddr*, socklen_t*)’
----
Source code:


```
#include <stdio.h>
#include <sys/types.h>
#include <sys/socket.h>
#include <netinet/in.h>
#include <arpa/inet.h>
#include <stdlib.h>
#include <unistd.h>
#include <errno.h>
#include <string.h>

int main(int argc,char *argv[])
{
int s, fd, len;
struct sockaddr_in my_addr;
struct sockaddr_in remote_addr;
int sin_size;

const char* buf[BUFSIZ];

memset(&my_addr, 0, sizeof(my_addr));
my_addr.sin_family = AF_INET;
my_addr.sin_addr.s_addr = INADDR_ANY;
my_addr.sin_port = htons (8000);

if ((s = socket(AF_INET, SOCK_STREAM, 0))<0)
{
perror("socket");
return 1;
}

if (bind(s, (struct sockaddr *)&my_addr,sizeof(struct sockaddr)) < 0)
{
perror("bind");
return 1;
}

listen(s, 5);
sin_size = sizeof(struct sockaddr_in);
/* HERE IS THE ERORR */
if ( (fd = accept(s, (struct sockaddr *)&remote_addr, &sin_size)) < 0)
{
perror("accept");
return 1;
}

printf("accepted client %s\n", inet_ntoa(remote_addr.sin_addr));
len = send(fd, "Welcome to the server\n", 21, 0);
while ((len = recv(fd, buf, BUFSIZ, 0)) > 0)
{
buf[len] = "\0";
printf("%s\n",buf);
if (send(fd, buf, len, 0) < 0)
{
perror("write");
return 1;
}
}
close(fd);
close(s);
return 0;
}
```

Does anyone know how to fix this?

---

### Post by joker31174 on 2009-08-04
Never mind...

Found the solution:


```
#include <stdio.h>
#include <sys/types.h>
#include <sys/socket.h>
#include <netinet/in.h>
#include <arpa/inet.h>
#include <stdlib.h>
#include <unistd.h>
#include <errno.h>
#include <string.h>

int main(int argc,char *argv[])
{
int s, fd, len;
struct sockaddr_in my_addr;
struct sockaddr_in remote_addr;
int sin_size;


const char* buf[BUFSIZ];

memset(&my_addr, 0, sizeof(my_addr));
my_addr.sin_family = AF_INET;
my_addr.sin_addr.s_addr = INADDR_ANY;
my_addr.sin_port = htons (8000);

if ((s = socket(AF_INET, SOCK_STREAM, 0))<0)
{
perror("socket");
return 1;
}

if (bind(s, (struct sockaddr *)&my_addr,sizeof(struct sockaddr)) < 0)
{
perror("bind");
return 1;
}

listen(s, 5);
sin_size = sizeof(struct sockaddr_in);
/* THIS LINE!!!*/
if ( (fd = accept(s, (struct sockaddr *)&remote_addr, (socklen_t *) &sin_size)) < 0)/*HOW DID I NOT GET THAT?*/
{
perror("accept");
return 1;
}

printf("accepted client %s\n", inet_ntoa(remote_addr.sin_addr));
len = send(fd, "Welcome to the server\n", 21, 0);
while ((len = recv(fd, buf, BUFSIZ, 0)) > 0)
{
buf[len] = "\0";
printf("%s\n",buf);
if (send(fd, buf, len, 0) < 0)
{
perror("write");
return 1;
}
}
close(fd);
close(s);
return 0;
}
```

---

