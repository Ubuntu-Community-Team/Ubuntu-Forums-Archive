---
title: "can't link source and object file in ubuntu"
date: 2012-12-19
forum: Programming Talk
---

### Post by sanda199 on 2012-12-19
Hi everyone, I need you help. I can't link source and object file in ubuntu. I wrote my c program in text editor and tried to compile. But at that time the terminal showed "Assembler messages: Fatal error: can't create server.o: Invalid argument".


Please help me. Thanks for your kindness

---

### Post by Bachstelze on 2012-12-19
Show your code, the commands you are running, and their output. *All* of it, not just what *you* think is relevant.

---

### Post by sanda199 on 2012-12-19
Here is my code:

```
#include<stdio.h>
#include<stdlib.h>
#include<string.h>
#include<unistd.h>
#include<sys/types.h>
#include<sys/socket.h>
#include<netinet/in.h>

void error(const char *msg) 
{
      perror(msg);
      exit(1);
}

int main(int argc, char *argv[])
{
      int sockfd, newsockfd, portno, clilen,n;
      char buffer[256];
      struct sockaddr_in serv_addr, cli_addr;
      if (argc<2)
      {
            fprintf(stderr, "ERROR, no port provided\n");
            exit(1);
      }
      sockfd=socket(AF_INET, SOCK_STREAM, 0);
      if(sockfd<0)
      {
            error("ERROR opening socket");
      }
      bzero((char *)&serv_addr, sizeof(serv_addr));
      portno=atoi(argv[1]);
      serv_addr.sin_family=AF_INET;
      serv_addr.sin_addr.s_addr=INADDR_ANY;
      serv_addr.sin_port=htons(portno);
      if(bind(sockfd,(struct sockaddr *)&serv_addr,sizeof(serv_addr))<0)
      {
            error("ERROR on binding");
      }
      listen(sockfd,5);
      clilen=sizeof(cli_addr);
      newsockfd=accept(sockfd,(struct sockaddr *)&cli_addr, &clilen);
      if(newsockfd<0)
      {
            error("ERROR on accept");
      }
      bzero(buffer,256);
      n=read(newsockfd,buffer,255);
      if(n<0)
      {
            error("ERROR reading from socket");
      }
      printf("Here is the message: %s\n",buffer);
      n=write(newsockfd,"I got your message", 18);
      if(n<0)
      {
            error("ERROR writing to socket");
      }
      close(newsockfd);
      close(sockfd);
      return 0;
}

```
This is my server.c program. and I type 

```
gcc -c server.c in terminal
```
after that the terminal showed[/FONT]

```
Assembler messages:
Fatal error: can't create server.o: Invalid argument
```
Thanks for your help.

---

### Post by zombifier25 on 2012-12-19
Try removing the "-c" flag from your compile command.

---

### Post by Bachstelze on 2012-12-19
> **zombifier25 said:**
> Try removing the "-c" flag from your compile command.

The -c flag is not the problem, I think OP didn't tell us all there is to it but I stopped caring when I saw all his threads.

---

### Post by steeldriver on 2012-12-19
> **sanda199 said:**
> This is my server.c program. [COLOR=Red][B]and I type 
[/B][/COLOR]
```
gcc -c server.c [COLOR=Red]**in terminal**[/COLOR]
```after that the terminal showed[/FONT]

```
Assembler messages:
Fatal error: can't create server.o: [COLOR=Red]**Invalid argument**[/COLOR]
```Thanks for your help.
...

---

### Post by linuxonbute on 2012-12-22
His code compiles fine for me using his syntax so probably he hasn't got everything he needs installed or he isn't in the directory where server.c is is when he tries the compile;)

---

