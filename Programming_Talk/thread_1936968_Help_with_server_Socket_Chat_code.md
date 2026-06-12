---
title: "Help with server Socket Chat code"
date: 2012-03-06
forum: Programming Talk
---

### Post by geewhan on 2012-03-06
Hey guys, I am writing a code for a server where it would recognize multiple clients. So far I am getting an error "Segmentation fault" when I run this code. I believe it is from this line of code:

```

for(p = ai; p != NULL; p = p->ai_next){

```

I made some modification to the original code that was taken off the site. So I assume the way I wrote it may conflict how the code runs.


Thank you for your time

Note: this is not a homework/project assignment. I just want to get an understanding of Socket programming.

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

#include <arpa/inet.h>
#include <netdb.h>

void error(const char *msg)
{
    perror(msg);
    exit(1);
}

int main(int argc, char *argv[])
{
     fd_set master;    // master file descriptor list
     fd_set read_fds;  // temp file descriptor list for select()
     int fdmax;        // maximum file descriptor number

     int sockfd, newsockfd, portno;
     socklen_t clilen;
     char buffer[256];
     int yes=1; //for setsockopt
     struct sockaddr_in serv_addr, cli_addr;
     int i, j, rv;
     int nbytes;
     char remoteIP[INET6_ADDRSTRLEN];
     struct addrinfo hints, *ai, *p;
     FD_ZERO(&master);    // clear the master and temp sets
     FD_ZERO(&read_fds);

     if (argc < 2) {
         fprintf(stderr,"ERROR, no port provided\n");
         exit(1);
     }

     bzero((char *) &serv_addr, sizeof(serv_addr));
     portno = atoi(argv[1]);
     serv_addr.sin_family = AF_INET;
     serv_addr.sin_addr.s_addr = INADDR_ANY;
     serv_addr.sin_port = htons(portno);

     for(p = ai; p != NULL; p = p->ai_next){
         sockfd = socket(AF_INET, SOCK_STREAM, 0);
         if (sockfd < 0){
	     continue;
         }
	//printf("The value for sockfd is %d \n", sockfd);
     //if (sockfd < 0) 
       // error("ERROR opening socket");

     	 if (setsockopt(sockfd,SOL_SOCKET,SO_REUSEADDR,
              &yes,sizeof(int)) == -1) {
    	      error("setsockopt");
    	      exit(1);
     	 }
	
    	 if (bind(sockfd, (struct sockaddr *) &serv_addr,
             sizeof(serv_addr)) < 0){ 
             close(sockfd);
	     continue;
         }
	     break;
     }


     if (listen(sockfd,5) == -1)
     {
         error("ERROR on listen");
	 exit(3);
     }

    // add the sockfd to the master set
    FD_SET(sockfd, &master);
    // keep track of the biggest file descriptor
    fdmax = sockfd; // so far, it's this one
    // main loop
    for(;;) {
        read_fds = master; // copy it
        if (select(fdmax+1, &read_fds, NULL, NULL, NULL) == -1) {
            perror("select");
            exit(4);
        }
//printf("We are at before the main for loop");
    for(i = 0; i <= fdmax; i++) {
        if (FD_ISSET(i, &read_fds)) { // we got one!!
            if (i == sockfd) {
                // handle new connections

     		clilen = sizeof(cli_addr);
    		 newsockfd = accept(sockfd, 
                 (struct sockaddr *) &cli_addr, 
                 &clilen);

     		if (newsockfd < 0) 
          	    error("ERROR on accept");
			else {
                        FD_SET(newsockfd, &master); // add to master set
                        if (newsockfd > fdmax) {    // keep track of the max
                            fdmax = newsockfd;
                        }
                        printf("selectserver: new connection from %s on "
                            "socket %d\n",
                            inet_ntop(AF_INET,
                                &(serv_addr.sin_addr),
                                remoteIP, INET6_ADDRSTRLEN),
                            newsockfd);
                    }
                } else {
                    // handle data from a client
                    if ((nbytes = recv(i, buffer, sizeof buffer, 0)) <= 0) {
                        // got error or connection closed by client
                        if (nbytes == 0) {
                            // connection closed
   			printf("selectserver: socket %d hung up\n", i);
                        } else {
                            error("recv");
                        }
                        close(i); // bye!
                        FD_CLR(i, &master); // remove from master set
                    } else {
                        // we got some data from a client
                        for(j = 0; j <= fdmax; j++) {
                            // send to everyone!
                            if (FD_ISSET(j, &master)) {
                                // except the sockfd and ourselves
                                if (j != sockfd && j != i) {
                                    if (send(j, buffer, nbytes, 0) == -1) {
                                        error("send");
                                    }
                                }
                            }
                        }
                    }
                } // END handle data from client
            } // END got new incoming connection
        } // END looping through file descriptors
    } // END for(;;)--and you thought it would never end!
    
    return 0;

}//End of main 


```

---

### Post by Hetepeperfan on 2012-03-07
I can see you declare the  ai and p variable as a pointer to struct addrinfo. However I can't find the spot where you initialize them. So uninitialized pointers point to problems.

So first make them point to something usefull then use them.

cheers.

---

### Post by geewhan on 2012-03-07
When you are referring where the ai is pointing I assume this part of code tells where it is pointing:

```
    memset(&hints, 0, sizeof hints);
    hints.ai_family = AF_UNSPEC;
    hints.ai_socktype = SOCK_STREAM;
    hints.ai_flags = AI_PASSIVE;
    if ((rv = getaddrinfo(NULL, PORT, &hints, &ai)) != 0) {
        fprintf(stderr, "selectserver: %s\n", gai_strerror(rv));
        exit(1);
    }
```


Though could you or someone explain to me what this part of code is doing, especially the for condition:

```
     for(p = ai; p != NULL; p = p->ai_next){
         sockfd = socket(AF_INET, SOCK_STREAM, 0);
         if (sockfd < 0){
	     continue;
         }
	//printf("The value for sockfd is %d \n", sockfd);
     //if (sockfd < 0) 
       // error("ERROR opening socket");


     	 if (setsockopt(sockfd,SOL_SOCKET,SO_REUSEADDR,
              &yes,sizeof(int)) == -1) {
    	      error("setsockopt");
    	      exit(1);
     	 }
	
    	 if (bind(sockfd, (struct sockaddr *) &serv_addr,
             sizeof(serv_addr)) < 0){ 
             close(sockfd);
	     continue;
         }
	     break;
     }
```

Thanks for your time

---

### Post by Hetepeperfan on 2012-03-08
[FONT=monospace]Hi Geewhan,

I was talking about this bit

[/FONT]```
     struct addrinfo hints, *ai, *p;
     FD_ZERO(&master);    // clear the master and temp sets
     FD_ZERO(&read_fds);

     if (argc < 2) {
         fprintf(stderr,"ERROR, no port provided\n");
         exit(1);
     }

     bzero((char *) &serv_addr, sizeof(serv_addr));
     portno = atoi(argv[1]);
     serv_addr.sin_family = AF_INET;
     serv_addr.sin_addr.s_addr = INADDR_ANY;
     serv_addr.sin_port = htons(portno);

     for(p = ai; p != NULL; p = p->ai_next){

```[FONT=monospace]

The next code should improve the code a little however.
I supopse the socket library provide functions or static
initializer macro's to initialize a struct addrinfo *.


[/FONT]```
     struct addrinfo hints, *ai = NULL, *p = NULL;
     
     ai = (struct addrinfo*) malloc (sizeof (struct addrinfo) );
     if (!ai)
         return1;
     p = (struct addrinfo*) malloc (sizeof (struct addrinfo) );
     if (!p)
         return1;
    
     FD_ZERO(&master);    // clear the master and temp sets
     FD_ZERO(&read_fds);

     if (argc < 2) {
         fprintf(stderr,"ERROR, no port provided\n");
         exit(1);
     }

     bzero((char *) &serv_addr, sizeof(serv_addr));
     portno = atoi(argv[1]);
     serv_addr.sin_family = AF_INET;
     serv_addr.sin_addr.s_addr = INADDR_ANY;
     serv_addr.sin_port = htons(portno);

     for(p = ai; p != NULL; p = p->ai_next){



```you might want to spit that code into manageable pieces.
I'm no socket expert so can't help you much further.

---

### Post by dwhitney67 on 2012-03-08
> **geewhan said:**
> When you are referring where the ai is pointing I assume this part of code tells where it is pointing:

```
    memset(&hints, 0, sizeof hints);
    hints.ai_family = AF_UNSPEC;
    hints.ai_socktype = SOCK_STREAM;
    hints.ai_flags = AI_PASSIVE;
    if ((rv = getaddrinfo(NULL, PORT, &hints, &ai)) != 0) {
        fprintf(stderr, "selectserver: %s\n", gai_strerror(rv));
        exit(1);
    }
```

Yes, getaddrinfo() will fill in ai if your PORT and hints are usable.  Why didn't you include the code above in your first post??

> **geewhan said:**
> 
Though could you or someone explain to me what this part of code is doing, especially the for condition:

```
     for(p = ai; p != NULL; p = p->ai_next){
         sockfd = socket(AF_INET, SOCK_STREAM, 0);
         if (sockfd < 0){
	     continue;
         }
	//printf("The value for sockfd is %d \n", sockfd);
     //if (sockfd < 0) 
       // error("ERROR opening socket");


     	 if (setsockopt(sockfd,SOL_SOCKET,SO_REUSEADDR,
              &yes,sizeof(int)) == -1) {
    	      error("setsockopt");
    	      exit(1);
     	 }
	
    	 if (bind(sockfd, (struct sockaddr *) &serv_addr,
             sizeof(serv_addr)) < 0){ 
             close(sockfd);
	     continue;
         }
	     break;
     }
```

Thanks for your time

Based on possible results from getaddrinfo(), an attempt is made to open a socket, and ultimately bind it using port/address information contained in the sockaddr_in serv_addr.  If the bind fails, then an attempt is made using the next sockaddr_in within the list that was returned by getaddrinfo().

You should be reading this [guide]("http://beej.us/guide/bgnet/output/html/singlepage/bgnet.html") to sockets, written by Beej.  A lot of your questions will be answered there.

---

### Post by geewhan on 2012-03-08
dwhitney, 

Like you mention on the Beej's site. I copied this exact same code that he wrote, but made some modifications. His codes are located on pg 37-40 in the pdf form.

Beej used int main(void), which seems that you need to use the getaddrinfo(NULL, PORT, &hints, &ai) code.

I use the int main(int argc, char *argv[]), which I assume you do not need to use getaddrinfo(NULL, PORT, &hints, &ai) code.

Currently the code runs, but I do not completely understand how each commands are written. I will re read Beej's  paper.

Though I am getting a different result. When I run my code and telnet for the client (I type telnet 127.0.0.1 port#). The server prints out 
> selectserver: new connection from 0.0.0.0 on socket 4  
As you can see it should not print 0.0.0.0 instead it should have print 127.0.0.1

I believe it has to do something with the inet_ntop command, but I am not sure if I set it up correctly.
```
printf("selectserver: new connection from %s on " "socket %d\n",
inet_ntop(AF_INET, &(serv_addr.sin_addr),remoteIP, INET6_ADDRSTRLEN), newsockfd);
```

Thanks for your time.

---

### Post by pconroy on 2012-03-08
> **geewhan said:**
> 
Beej used int main(void), which seems that you need to use the getaddrinfo(NULL, PORT, &hints, &ai) code.

I use the int main(int argc, char *argv[]), which I assume you do not need to use getaddrinfo(NULL, PORT, &hints, &ai) code.



You lost me completely on this statement.
You know what argc, argv are, correct?

When you get a SEG Fault in 'C', 99% of the time, you look for an uninitialized pointer.

This line:
getaddrinfo(NULL, PORT, &hints, &ai) code.

passes in the address of the ai ptr and fills it out.

The previous poster is correct, that if you declare ai to be a *ptr, you'd better (m)allocate memory for it.

---

### Post by dwhitney67 on 2012-03-08
> **pconroy said:**
> ... if you declare ai to be a *ptr, you'd better (m)allocate memory for it.

No, there's no need to do this.  getaddrinfo() allocates the memory for the linked-list that is returned, if of course, the function is successful.

---

### Post by dwhitney67 on 2012-03-08
.

---

### Post by dwhitney67 on 2012-03-08
> **geewhan said:**
> 
```
printf("selectserver: new connection from %s on " "socket %d\n",
inet_ntop(AF_INET, &(serv_addr.sin_addr),remoteIP, INET6_ADDRSTRLEN), newsockfd);
```


Hmmm... I'm not quite sure what "version" of inet_ntop() you are calling.  Typically this function only accepts 4 parameters (the first 4 that you have specified); I'm not sure what impact that 5th parameter is having.  Didn't the compiler issue a warning?
-------

Edit:  Never mind... it's late and I am apparently having trouble matching parenthesis.  The code above is fine.

Btw, what is the size of the remoteIP buffer?

---

### Post by geewhan on 2012-03-09
dwhitney,

> Btw, what is the size of the remoteIP buffer?

I initialize it here and I believe the size is 46
```
char remoteIP[INET6_ADDRSTRLEN]; 
```

I was thinking the same thing about INET6_ADDRSTRLEN because this is for IPv6, so for IPv4 it is 
```
char remoteIP[INET_ADDRSTRLEN]; 
```

However this gives me an error:

> ERROR on listen: Bad file descriptor

Which I do not understand why the listen would be bad if I just change the IP version

---

### Post by dwhitney67 on 2012-03-09
Here's a simple example:
```

#include <sys/socket.h>
#include <arpa/inet.h>
#include <string.h>
#include <unistd.h>
#include <errno.h>
#include <stdio.h>


int main(void)
{
    int sd = socket(AF_INET, SOCK_STREAM, IPPROTO_TCP);

    struct sockaddr_in sin;

    memset(&sin, 0, sizeof(sin));
    sin.sin_family      = AF_INET;
    sin.sin_addr.s_addr = INADDR_ANY;
    sin.sin_port        = htons(9000);

    int res = bind(sd, (struct sockaddr*) &sin, sizeof(sin));

    if (res != 0)
    {
        fprintf(stderr, "%s [%d]\n", strerror(errno), errno);
    }

    listen(sd, 5);

    struct sockaddr_in client_sin;
    socklen_t          client_sin_len = sizeof(client_sin);

    int client_sd = accept(sd, (struct sockaddr*) &client_sin, &client_sin_len);

    if (client_sd != -1)
    {
        char buf[INET6_ADDRSTRLEN + 1];

        printf("Client at %s just connected.\n",
               inet_ntop(AF_INET, &(client_sin.sin_addr), buf, sizeof(buf)));

        close(client_sd);
    }

    close(sd);

    return 0;
}

```

---

