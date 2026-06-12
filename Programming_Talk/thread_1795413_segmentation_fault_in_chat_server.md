---
title: "segmentation fault in chat server"
date: 2011-07-02
forum: Programming Talk
---

### Post by kapil1503 on 2011-07-02
hello, i am making a tcp chat sever using c in linux for multiple clients.i have made the program but there occurs segmentation fault on the client side. could anyone please tell me how to remove it??
also i would appreciate if anyone could guide me what to do to ensure private chatting also in my program. till now only group chatting takes place. thanks!

---

### Post by cgroza on 2011-07-02
Use gdb to track it down. Also, make sure that your pointers are valid and you are not double freeing them.

---

### Post by dwhitney67 on 2011-07-02
Because I'm sick and tired of lazy folks not posting their code...

```

#include <stdio.h>
#include <unistd.h>
#include <stdlib.h>
#include <string.h>
#include <sys/types.h>
#include <sys/socket.h>
#include <netinet/in.h>
#include <netdb.h>

#define MSG_SIZE 80
#define MAX_CLIENTS 95
#define MYPORT 7400

int main(int argc, char *argv[]) {
   
   
   int port;
   int client_sockfd;
   struct sockaddr_in server_address;
   int addresslen = sizeof(struct sockaddr_in);
   int fd;
   char fd_array[MAX_CLIENTS];
   fd_set readfds, testfds, clientfds;
   char msg[MSG_SIZE + 1];     
   char kb_msg[MSG_SIZE + 10]; 
   
   /*Client variables*/
   int sockfd;
   int result;
   char hostname[MSG_SIZE];
   struct hostent *hostinfo;
   struct sockaddr_in address;
   char alias[MSG_SIZE];
   int clientid;
   
   /*Client*/
   if(argc==2 || argc==4){
     if(!strcmp("-p",argv[1])){
       if(argc==2){
         printf("Invalid parameters.\nUsage: chat [-p PORT] HOSTNAME\n");
         exit(0);
       }else{
         sscanf(argv[2],"%i",&port);
         strcpy(hostname,argv[3]);
       }
     }else{
       port=MYPORT;
       strcpy(hostname,argv[1]);
     }
  
     printf("\n*** Client program starting (enter \"quit\" to stop): \n");

     /* Create a socket for the client */
     sockfd = socket(AF_INET, SOCK_STREAM, 0);

     /* Name the socket, as agreed with the server */
     hostinfo = gethostbyname(hostname);  /* look for host's name */
     address.sin_addr = *(struct in_addr *)*hostinfo -> h_addr_list;
     address.sin_family = AF_INET;
     address.sin_port = htons(port);

     /* Connect the socket to the server's socket */
     if(connect(sockfd, (struct sockaddr *)&address, sizeof(address)) < 0){
       perror("connecting");
       exit(1);
     
     
     fflush(stdout);
     
     FD_ZERO(&clientfds);
     FD_SET(sockfd,&clientfds);
     FD_SET(0,&clientfds);//stdin
     
     /*  Now wait for messages from the server */
     while (1) {
       testfds=clientfds;
       select(FD_SETSIZE,&testfds,NULL,NULL,NULL);
       
       for(fd=0;fd<FD_SETSIZE;fd++){
          if(FD_ISSET(fd,&testfds)){
             if(fd==sockfd){   /*Accept data from open socket */
                //printf("client - read\n");
                
                //read data from open socket
                result = read(sockfd, msg, MSG_SIZE);
                msg[result] = '\0';  /* Terminate string with null */
                printf("%s", msg+1);
                
                if (msg[0] == 'X') {                   
                    close(sockfd);
                    exit(0);
                }                             
             }
             else if(fd == 0){ /*process keyboard activiy*/
               // printf("client - send\n");
                
                fgets(kb_msg, MSG_SIZE+1, stdin);
                //printf("%s\n",kb_msg);
                if (strcmp(kb_msg, "quit\n")==0) {
                    sprintf(msg, "XClient is shutting down.\n");
                    write(sockfd, msg, strlen(msg));
                    close(sockfd); //close the current client
                    exit(0); //end program
                }
                else {
                   /* sprintf(kb_msg,"%s",alias);
                    msg[result]='\0';
                    strcat(kb_msg,msg+1);*/

                    sprintf(msg, "M%s", kb_msg);

                    write(sockfd, msg, strlen(msg));
                }                                                 
             }          
          }
	 }
       }      
     }
   }// end client code   
}//main

```

---

### Post by dwhitney67 on 2011-07-02
Avoid these functions: strcat(), strcpy(), and sprintf().

Use:  strncat(), strncpy(), and snprintf().

Check your code to ensure that you do not overrun any of your buffers, such as could possibly happen with this nugget:
```

sprintf(msg, "M%s", kb_msg);

```

---

### Post by kapil1503 on 2011-07-03
hello,
i tried using strncat, snprintf and strncpy but it gives the error that there are too few arguments for it.

---

### Post by kapil1503 on 2011-07-03
hello 
i tried tracking down with gdb but it was not successful. i have checked al the pointers. they are valid.

---

### Post by dwhitney67 on 2011-07-03
I could not get your program to crash at all; I ran the code below, which for the most part is yours but with some minor corrections/enhancements which I have marked in bold text.  I also reorganized the curly brackets so that if an anomaly is detected (e.g. user input or connect), the program exits immediately.

```

#include <stdio.h>
#include <unistd.h>
#include <stdlib.h>
#include <string.h>
#include <sys/types.h>
#include <sys/socket.h>
#include <netinet/in.h>
#include <netdb.h>

#define MSG_SIZE 80
#define MAX_CLIENTS 95
#define MYPORT 7400

int main(int argc, char* argv[])
{
   int port;
   int fd;
   fd_set testfds, clientfds;
   char msg[MSG_SIZE + 1];
   char kb_msg[MSG_SIZE + 10];

   /*Client variables*/
   int sockfd;
   int result;
   //char hostname[MSG_SIZE];
   **char* hostname = NULL;**
   struct hostent* hostinfo;
   struct sockaddr_in address;

   /*Client*/
   if (argc == 2 || argc == 4)
   {
      if (!strcmp("-p", argv[1]))
      {
         if (argc == 2)
         {
            printf("Invalid parameters.\nUsage: chat [-p PORT] HOSTNAME\n");
            exit(0);
         }
         else
         {
            sscanf(argv[2], "%i", &port);
            //strcpy(hostname, argv[3]);
            **hostname = argv[3];**
         }
      }
      else
      {
         port = MYPORT;
         //strcpy(hostname, argv[1]);
         **hostname = argv[1];**
      }
   }
[B]   else
   {
      printf("Invalid parameters.\nUsage: chat [-p PORT] HOSTNAME\n");
      exit(0);
   }[/B]

   printf("\n*** Client program starting (enter \"quit\" to stop): \n");

   /* Create a socket for the client */
   sockfd = socket(AF_INET, SOCK_STREAM, 0);

   /* Name the socket, as agreed with the server */
   hostinfo = gethostbyname(hostname);  /* look for host's name */
   **memset(&address, 0, sizeof(address));**
   address.sin_addr   = *(struct in_addr*)*hostinfo->h_addr_list;
   address.sin_family = AF_INET;
   address.sin_port   = htons(port);

   /* Connect the socket to the server's socket */
[B]   if (connect(sockfd, (struct sockaddr*)&address, sizeof(address)) != 0)
   {
      perror("connecting");
      exit(1);
   }[/B]

   FD_ZERO(&clientfds);
   FD_SET(sockfd, &clientfds);
   **FD_SET(fileno(stdin), &clientfds);**

   /*  Now wait for messages from the server */
   while (1)
   {
      testfds = clientfds;
      select(FD_SETSIZE, &testfds, NULL, NULL, NULL);

      for (fd = 0; fd < FD_SETSIZE; fd++)   **/* necessary??? */**
      {
         if (FD_ISSET(fd, &testfds))
         {
            if (fd == sockfd)    /*Accept data from open socket */
            {
               //read data from open socket
               result = read(sockfd, msg, MSG_SIZE);
               msg[result] = '\0';  /* Terminate string with null */
               printf("%s", msg + 1);

               if (msg[0] == 'X')
               {
                  close(sockfd);
                  exit(0);
               }
            }
            **else if (fd == fileno(stdin))**  /*process keyboard activiy*/
            {
               **fgets(kb_msg, sizeof(kb_msg) - 1, stdin);**

               if (strcmp(kb_msg, "quit\n") == 0)
               {
                  sprintf(msg, "XClient is shutting down.\n");
                  write(sockfd, msg, strlen(msg));
                  close(sockfd); //close the current client
                  exit(0); //end program
               }
               else
               {
                  **snprintf(msg, sizeof(msg) - 1, "M%s", kb_msg);**
                  write(sockfd, msg, strlen(msg));
               }
            }
         }
      }
   }

   return 0;
}

```
I left most of the unsafe functions in place; you should reference the man-page for the API of the sister functions I wrote of earlier.

Btw, gethostbyname() is obsolete.  Use getaddrinfo() instead.  See the man-page!

---

