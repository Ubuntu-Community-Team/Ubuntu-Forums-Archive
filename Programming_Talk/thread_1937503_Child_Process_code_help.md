---
title: "Child Process code help"
date: 2012-03-07
forum: Programming Talk
---

### Post by geewhan on 2012-03-07
Hey guys, I am writing a code for a server where it would recognize multiple clients. So far the code runs, but does not recognize the child. Does anyone know the reason why?

Thank you for your time

```
/* A simple server in the internet domain using TCP
   The port number is passed as an argument */
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <unistd.h>
#include <sys/types.h> 
#include <sys/socket.h>
#include <netinet/in.h>

#include <sys/wait.h>

void error(const char *msg)
{
    perror(msg);
    exit(1);
}

int main(int argc, char *argv[])
{
     int sockfd, newsockfd, portno;
     socklen_t clilen;
     char buffer[256];
     char tmp[256];
     char * ptr;
     struct sockaddr_in serv_addr, cli_addr;
     int n, sent, length;
     pid_t processid;
     int childcount = 0;

     if (argc < 2) {
         fprintf(stderr,"ERROR, no port provided\n");
         exit(1);
     }

     //Step 1: Create a socket
     sockfd = socket(AF_INET, SOCK_STREAM, 0);
     if (sockfd < 0) 
        error("ERROR opening socket");

     //Step 2: Setup Address structure
     bzero((char *) &serv_addr, sizeof(serv_addr));
     portno = atoi(argv[1]);
     serv_addr.sin_family = AF_INET;
     serv_addr.sin_addr.s_addr = INADDR_ANY;
     serv_addr.sin_port = htons(portno);

     //Step 3: Bind the socket to the port
     if (bind(sockfd, (struct sockaddr *) &serv_addr,
              sizeof(serv_addr)) < 0) 
              error("ERROR on binding");

     //Step 4:Listen to the socket
     listen(sockfd,5);

     //Step 5: Setup an infinite loop to make connections
     while(1){
           clilen = sizeof(cli_addr);
           newsockfd = accept(sockfd, 
                 (struct sockaddr *) &cli_addr, 
                 &clilen);
           if (newsockfd < 0) 
             error("ERROR on accept");

           printf("Client Accepted!");

   //fork this process into a child and parent
	   processid = fork();
printf("Child! %d", processid);
   //Check the return value given by fork(), if negative then error,
   //if 0 then it is the child.
	   if ( processid == -1){
	       error("fork()");
	   }else if (processid == 0){
	     /*Child Process*/

		   close(sockfd);
		//loop until client closes
		    while (1){
			//read string from client
    			 bzero(buffer,256);
			 do{
			   bzero(tmp,256);
			   tmp[n] = '\0';
			   n = read(newsockfd,tmp,255);
   			   if (n < 0) error("ERROR reading from socket");
			   if (n == 0) break;
			   strncat(buffer, tmp, n-1);
			   buffer[n-1] = ' ';
			 }while (tmp[n-1] != '\n');
			 buffer[ strlen(buffer) ] = '\n';
				
			 if (n == 0) break;
				    			 
 			 //write string back to client
			 sent = 0;
			 ptr = buffer;
			 length = strlen(buffer);
			 while (sent < length ){
		         	n = write(newsockfd, ptr, strlen(ptr) );	
     				if (n < 0) error("ERROR writing to socket");
			 sent += n;
			 ptr += n;
			 }
		   }
     		   close(newsockfd);
     		   //Child Exits
     		   exit(0);
      		 }//End of if statement processid

      //Parent Process
      printf("Child process spawned with id number: %d\n",processid);

     //increment the number of children processes
     childcount++;

     while(childcount){
	   processid = waitpid( (pid_t) - 1, NULL, WNOHANG );
	   if (processid < 0) error("waitpid()");
	   else if (processid == 0) break;
		  else childcount--;
     }
	
     }//End of Main While loop
     close(sockfd);
     exit(0); 
}

```

---

