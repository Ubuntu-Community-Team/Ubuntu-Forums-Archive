---
title: "[Network Programming] Problem with select() function"
date: 2010-09-17
forum: Programming Talk
---

### Post by moby@root on 2010-09-17
Hi,
 This is my first post so at first I want to say thanks to those who  created this forum and those who support it with their knowledge.

 I've installed Ubuntu Netbook 10 (inside windows) a couple of days ago  and started practicing network programming in Linux. there are many  shared points between socket programming in Windows and Linux so I could  write my first network program in Linux and run it easily but today I  encountered a problem that is driving me mad.

 Problem is the below code which is supposed to handle multiple  connections using select() function.


```

/*server.c--A TCP server that accept connections on port 5555. */
#include <stdio.h>
#include <stdlib.h>
#include <stdbool.h>
#include <string.h>
#include <sys/types.h>
#include <sys/socket.h>
#include <netinet/in.h>
#include <unistd.h>
#include <errno.h>
#define BUFF_SIZE 128
#define BACKLOG_SIZE 3

void addsocket(int sockfd, int *socketsarray, int *lastindex);
void removesocket(int sockindex,int *socketsarray, int *lastindex);


 int main()
 {
  int result,i,bytes_recv; 
  // sockets_num holds the allsockets array last index.
  int sockets_num=-1;
  int listensocket,acceptsocket,allsockets[32];
  char buff[BUFF_SIZE];
  fd_set readable_set,allsockets_set;
  socklen_t clientaddr_size;
  struct sockaddr_in serveraddr,clientaddr;

   listensocket = socket(AF_INET, SOCK_STREAM, 0);
   if(listensocket == -1) {
    printf("Unable to create new socket.%s\n",strerror(errno));
    exit(0x01);
   }

   serveraddr.sin_family = AF_INET;
   serveraddr.sin_port = htons(5555);
   serveraddr.sin_addr.s_addr = INADDR_ANY;

   result = bind(listensocket, (struct sockaddr *) &serveraddr, sizeof(serveraddr));
   if(result == -1) {
    printf("Unable to bind socket on local address.%s\n",strerror(errno));
    exit(0x02);
   }

   result = listen(listensocket,BACKLOG_SIZE);
   if(result == -1) {
    printf("listen function returned an error.%s\n",strerror(errno));
    exit(0x03);
   }

   clientaddr_size = sizeof(clientaddr);
   

   // add listensocket as the first socket to the allsockets array
   addsocket(listensocket,allsockets,&sockets_num);

   while(true)
   {
    FD_ZERO(&readable_set);
    // add all sockets to readable_set to see if they are readable or not
    for(i=0; i<=sockets_num ; i++)
     FD_SET(allsockets[i],&readable_set);

    FD_SET(listensocket,&allsockets_set);

    select(sockets_num+1, &readable_set, NULL, NULL, NULL);

    // check if sockets are readable or not
    for(i=0; i<=sockets_num ;i++)
    {
     if(FD_ISSET(allsockets[i],&readable_set))
     {
      // if the readable socket was the listener socket, there is an incoming connection
      if(allsockets[i] == listensocket)
      {
       acceptsocket = accept(listensocket, (struct sockaddr *) &clientaddr, (socklen_t *) &clientaddr);
       if(acceptsocket != -1) {
        printf("A new connection from %s\n", (char *)inet_ntoa(clientaddr.sin_addr.s_addr));
        addsocket(acceptsocket,allsockets,&sockets_num);
       } else {
        printf("Accepting new connection failed.%s\n",strerror(errno));
       }

      }
      else
      {
       // if the socket we are working on was not the listener socket, so there must an incoming message.
       bytes_recv = recv(allsockets[i], buff, BUFF_SIZE, 0);

       switch(bytes_recv)
       {
        case -1:
         printf("Unable to receive the clients message.%s\n",strerror(errno));
         break;

        case 0:
         printf("Client closed its connection.\n");
         close(allsockets[i]);
         removesocket(i,allsockets,&sockets_num);
         break;

        default:
         printf("New message:\n%s [%d Bytes]\n\n",buff,bytes_recv);

       }
 
      } // if(allsockets[i ... end


     } // if(FD_ISSET... end
      
     
    } // for end


   } // while end


  return 0;
 }


 void addsocket(int sockfd, int *socketsarray, int *lastindex)
 {
  
   // increment the lastinedx value.
   (*lastindex)++;
   
   // copy sockfd in the new index.
   socketsarray[*lastindex] = sockfd;

 }


 void removesocket(int sockindex,int *socketsarray, int *lastindex)
 {
  int i;
  
   // decrease the lastindex value.
   (*lastindex)--;

   // remove the specified index
   for(i=sockindex; i<=*lastindex ;i++)
    socketsarray[i] = socketsarray[i+1];

 }


``` I don't know what is the problem. When I run the program and connect to  it from another station, It accepts the connection and receives the  messages but there is no output on the screen. On the client side  everything seems to be okay. you can connect and send messages but there  is no reaction from the server.
 
 any comment or suggestion to fix the problem would make me happy,
 Thanks,
 moby

---

