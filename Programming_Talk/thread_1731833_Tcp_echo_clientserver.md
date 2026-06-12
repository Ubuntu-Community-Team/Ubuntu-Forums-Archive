---
title: "Tcp echo client/server"
date: 2011-04-17
forum: Programming Talk
---

### Post by greenmonkeey on 2011-04-17
> 
#include <stdio.h>
  #include <stdlib.h>
  #include <sys/types.h>
  #include <sys/socket.h>
  #include <netinet/in.h>
  #include <error.h>
  #include <arpa/inet.h>
  #include <unistd.h>
  #include <string.h>

#define ERROR -1
#define BUFFER 1024

   main(int argc, char **argv) {

 struct sockaddr_in remote_server;
 int sock;
 int input[BUFFER];
 int len;
 char output[BUFFER];

if((sock = socket(AF_INET,SOCK_STREAM, 0))==ERROR)

{
  perror(" socket");
  exit(-1);

}

remote_server.sin_family = AF_INET;
remote_server.sin_port = htons(atoi(argv[2]));
remote_server.sin_addr.s_addr = inet_addr(argv[1]);
bzero(&remote_server.sin_zero,0);

if((connect(sock,(struct sockaddr *)&remote_server,sizeof(struct sockaddr_in)))== ERROR)
{
    perror("connect");
     exit(-1);
}
while(1);
{
  fgets(input, BUFFER, stdin);
  send(sock,input, strlen(input), 0);
  len = recv(sock, output, BUFFER, 0);
   output[len] = '\0';
   printf("%s\n",output);

}
close(sock);

} 


hi this is my easy program but getting some warnings
  
clientserver.c: In function &#8216;main&#8217;:
clientserver.c:42: warning: passing argument 1 of &#8216;fgets&#8217; from incompatible pointer type
/usr/include/stdio.h:624: note: expected &#8216;char * __restrict__&#8217; but argument is of type &#8216;int *&#8217;
clientserver.c:43: warning: passing argument 1 of &#8216;strlen&#8217; from incompatible pointer type
/usr/include/string.h:399: note: expected &#8216;const char *&#8217; but argument is of type &#8216;int *&#8217;

---

### Post by greenmonkeey on 2011-04-17
pla let me know wats the prob here....i hv to submit my code tomorrow

---

### Post by greenmonkeey on 2011-04-17
i did it finally but when i write somethng on client terminal like"hello" it does not echoed back...wat i m missing tell me? i m r side giving u the code for server...

> 

  #include <stdio.h>
  #include <stdlib.h>
  #include <sys/types.h>
  #include <sys/socket.h>
  #include <netinet/in.h>
  #include <error.h>
  #include<strings.h>
  #include <arpa/inet.h>
  #include <unistd.h>

#define ERROR -1
#define MAX_CLIENTS 2
#define MAX_DATA 1024
 
   main(int argc, char **argv) {

 struct sockaddr_in server;
struct  sockaddr_in client;
 int sock;
int new;

int sockaddr_len = sizeof(struct sockaddr_in);
int data_len;
char data[MAX_DATA];

if((sock = socket(AF_INET,SOCK_STREAM, 0))==ERROR)

{
  perror("server socket");
  exit(-1);

}

server.sin_family = AF_INET;
server.sin_port = htons(atoi(argv[1]));
server.sin_addr.s_addr = INADDR_ANY;
bzero(&server.sin_zero,0);

if((bind(sock,(struct sockaddr *)&server,sockaddr_len))== ERROR)
{
    perror("bind: ");
     exit(-1);
}

if((listen(sock,MAX_CLIENTS))== ERROR)

{

  perror("listen");
  exit(-1);
}
while(1) //   

{

 if((new = accept(sock,(struct sockaddr *)&client,&sockaddr_len))==ERROR)
{
     perror("accept");
     exit(-1);
}

  printf("new client connected from port no %d and IP %s\n",ntohs(client.sin_port),inet_ntoa(client.sin_addr));

   data_len = 1;

    while(data_len)

   {

      data_len = recv(new, data, MAX_DATA,0);
      if(data_len)
{

 send(new,data,data_len, 0);
data[data_len] = '\0';
printf("sent mesg: %s",data);
}
}
printf("Client disconnected\n");
close(new);
}

}







---

### Post by dwhitney67 on 2011-04-18
> **greenmonkeey said:**
> i did it finally but when i write somethng on client terminal like"hello" it does not echoed back...wat i m missing tell me? i m r side giving u the code for server...

Could you please write in proper English?  This text-messaging style you use above is crap!  Be courteous to others if you wish for any help.

Also, when posting code, place it in CODE tags; that way, any indentation you may have in your code is preserved.

Fundamentally, there is nothing wrong with the server-side of your project, though I would be careful with the following:
```

data_len = recv(new, data, MAX_DATA,0);
if(data_len)

```
Don't assume that data_len is either 0 or greater than zero; it could be less than zero if an error occurs.

Here, don't assume data_len will be less than MAX_DATA; if it is MAX_DATA, then below you will have a buffer overrun.
```

data[data_len] = '\0';

```

Also, the following could be done better with a do-while loop:
```

...
data_len = 1;

while(data_len)

{
   ...
}

```

In conclusion, if your "echo" project isn't working to your satisfaction, then perhaps the issue is on the client-side.


P.S.  Declare main() to return an int, and return a value (say 0).

--------------------------------------------------------------------

EDIT:  This may be the issue:
```

server.sin_family = AF_INET;
server.sin_port = htons(atoi(argv[1]));
server.sin_addr.s_addr = INADDR_ANY;
bzero(&server.sin_zero,0);

```
Try this instead:
```

memset(&server, 0, sizeof(server));
server.sin_family = AF_INET;
server.sin_port = htons(atoi(argv[1]));
server.sin_addr.s_addr = INADDR_ANY;

```
bzero() was deprecated long ago; use memset() instead.  Also, it is best to clear out the sockaddr_in structure before using it.

---

