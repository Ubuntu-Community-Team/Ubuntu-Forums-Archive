---
title: "Network programming in c"
date: 2011-06-24
forum: Programming Talk
---

### Post by trnkumarchawla on 2011-06-24
I am just learning network programming in unix, I am writing a server and I want to bind my listening socket to a particular address and port ,but bind() function is throwing error and here is the code for server.

---

### Post by dwhitney67 on 2011-06-24
If you are running your app as a regular user, then you must use a port number greater than or equal to 1024.  Port numbers below this range are reserved for application that run with 'root' privileges.

P.S.  bzero() was deprecated long ago.  Use memset() instead.

---

### Post by nvteighen on 2011-06-25
There are other errors too... unless you're using the C++ compiler (g++)... which you shouldn't. Use gcc.

sockaddr_in is a struct type, so you have to use it this way when declaring something of that type:

```

struct sockaddr_in *variable_name*;

```

Leaving 'struct' aside is only allowed in C++, not in C.

Also, there are a couple of things you can do more easily these days. Filling sockaddr_in manually can be avoided by using a couple of functions. Take a look on this **great** tutorial: [http://beej.us/guide/bgnet/](http://beej.us/guide/bgnet/)

---

### Post by trnkumarchawla on 2011-06-26
I have used memset instead of bzero and used port number greater than 1024 but still showing same error.
I think bzero still works fine,and there is no problem with g++ it is the best. Please have a look at it again,I have just changed memset instead of bzero and increased the port number to 1030.

---

### Post by dwhitney67 on 2011-06-26
memset()... good.

bzero()... deprecated.

port number greater than or equal to 1024... good.

As nvteighen indicated, you need to choose if you wish to program in C or C++.  The title of the this thread indicates you wish to use C.  Thus you need to use the 'struct' keyword, where appropriate, in your code, and 'gcc' to compile the code, not 'g++'.

As for the bind(), it is failing because of this:
```

servaddr.sin_addr.s_addr = htonl(inet_addr("127.0.0.1"));

```
Change it to:
```

inet_aton("127.0.0.1", &servaddr.sin_addr);

```

Better yet, you should get into the habit of using getaddrinfo().  The man-page provides a good description of this function, and provides useful examples on how to use it.

---

### Post by trnkumarchawla on 2011-06-26
thnx sir ,it works but what is the problem with my code,i am doing the same thing but with a different function.

---

### Post by dwhitney67 on 2011-06-26
> **trnkumarchawla said:**
> thnx sir ,it works but what is the problem with my code,i am doing the same thing but with a different function.

Yes, I just experimented to find that the issue is with your use of htonl().  This would have sufficed:
```

servaddr.sin_addr.s_addr = inet_addr("127.0.0.1");

```

---

### Post by trnkumarchawla on 2011-06-26
sir you are a great teacher and thanking you very much for giving me your precious time.
now i have write a code for client also but it is not connctin with the server and server just waits when i run both programs on same machine.
i am giving the code for client and server both,just see it ,i am trying to resolve the problem.....

---

### Post by dwhitney67 on 2011-06-26
Here are working Server and Client applications.  Study them to glean some ideas.

Server.c:
```

#include <sys/types.h>
#include <sys/socket.h>
#include <netinet/in.h>
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <unistd.h>


void handleClient(int client);


int main(int argc, char** argv)
{
   if (argc != 2)
   {
      fprintf(stderr, "Usage: %s <port>\n", argv[0]);
      exit(EXIT_FAILURE);
   }

   const char* PORT = argv[1];

   // open socket
   int sockfd = socket(AF_INET, SOCK_STREAM, IPPROTO_TCP);

   if (sockfd == -1)
   {
      perror("Cannot open socket");
      exit(EXIT_FAILURE);
   }

   // bind socket
   struct sockaddr_in sin;
   memset(&sin, 0, sizeof(sin));
   sin.sin_family      = AF_INET;
   sin.sin_addr.s_addr = htonl(INADDR_ANY);
   sin.sin_port        = htons(atoi(PORT));

   int ret = bind(sockfd, (struct sockaddr*) &sin, sizeof(sin));

   if (ret != 0)
   {
      perror("Cannot bind socket");
      exit(EXIT_FAILURE);
   }

   // setup listen
   ret = listen(sockfd, 5);

   if (ret != 0)
   {
      perror("Cannot setup listen");
      exit(EXIT_FAILURE);
   }

   for (;;)
   {
      // accept client connection
      int client = accept(sockfd, NULL, NULL);

      printf("Client connected.\n");

      handleClient(client);
   }

   close(sockfd);

   return 0;
}


void handleClient(int client)
{
   char buf[1024];

   for (;;)
   {
      int bytes_rcvd = recv(client, buf, sizeof(buf) - 1, 0);

      if (bytes_rcvd > 0)
      {
         buf[bytes_rcvd] = '\0';

         fprintf(stdout, "Server Received: %s\n", buf);

         // send message back to client
         const char*  msg = "Your message was received.";
         const size_t msg_len = strlen(msg);
         size_t       bytes_sent = 0;

         while (bytes_sent < msg_len)
         {
            int ret = send(client, msg + bytes_sent, msg_len - bytes_sent, 0);

            if (ret > 0)
            {
               bytes_sent += ret;
            }
            else if (ret < 0)
            {
               perror("Error sending data to client.");
            }
         }
      }
      else if (bytes_rcvd == 0)
      {
         printf("Client disconnected.\n");
         break;   // client disconnected
      }
      else
      {
         perror("Error receiving from client.");
      }
   }

   close(client);
}

```

Client.c:
```

#include <sys/types.h>
#include <sys/socket.h>
#include <netinet/in.h>
#include <arpa/inet.h>
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <unistd.h>


void stripNewline(char* str);


int main(int argc, char** argv)
{
   if (argc != 3)
   {
      fprintf(stderr, "Usage: %s <host> <port>\n", argv[0]);
      exit(EXIT_FAILURE);
   }

   const char* HOST = argv[1];
   const char* PORT = argv[2];

   // open socket
   int sockfd = socket(AF_INET, SOCK_STREAM, IPPROTO_TCP);

   if (sockfd == -1)
   {
      perror("Cannot open socket");
      exit(EXIT_FAILURE);
   }

   // connect socket
   struct sockaddr_in sin;
   memset(&sin, 0, sizeof(sin));
   sin.sin_family      = AF_INET;
   sin.sin_addr.s_addr = inet_addr(HOST);
   sin.sin_port        = htons(atoi(PORT));

   int ret = connect(sockfd, (struct sockaddr*) &sin, sizeof(sin));

   if (ret != 0)
   {
      perror("Cannot connect socket");
      exit(EXIT_FAILURE);
   }

   for (;;)
   {
      char msg[1024];

      printf("Enter the message to send: ");
      fgets(msg, sizeof(msg), stdin);

      stripNewline(msg);

      send(sockfd, msg, strlen(msg), 0);

      int bytes_rcvd = recv(sockfd, msg, sizeof(msg) - 1, 0);

      if (bytes_rcvd > 0)
      {
         msg[bytes_rcvd] = '\0';
         printf("Client Received: %s\n\n", msg);
      }
      else if (bytes_rcvd == 0)
      {
         fprintf(stderr, "Server gave us the boot!\n");
         break;
      }
      else
      {
         perror("Error receiving.");
      }
   }

   close(sockfd);

   return 0;
}


void stripNewline(char* str)
{
   char* nl = strchr(str, '\n');

   if (nl)
   {
      *nl = '\0';
   }
}

```

---

### Post by trnkumarchawla on 2011-06-27
sir thnx again,now i have understood some of the basic concepts with ur example.
sir will u please explain the operation u have done with the recieved string and send string.
by operation that u always make sure that last character is '\0', i am little bit confused here as fgets stops reading till EOF or newline and automatically last character stored is '\0'.


simply please tell me the string operations u have done,if u don't mind.

sorry for any grammatical mistakes.....

---

### Post by PaulM1985 on 2011-06-27
'\0' is the termination character for a string.  Having this character lets fgets know when to stop reading.

Paul

---

### Post by dwhitney67 on 2011-06-27
> **trnkumarchawla said:**
> ... fgets stops reading till EOF or newline and automatically last character stored is '\0'.


That is correct.  However, if you read the documentation for fgets(), the newline character may also be stored in the buffer.  In certain instances, having a newline in the buffer is not desirable, hence the reason I replaced that particular character, if found, with a null character.

---

### Post by trnkumarchawla on 2011-06-27
I got it but I will post some more question when I will put server and client on different computer using a cross lan cable,till then good bye.
Thanking you all.
Tarun Chawla

---

