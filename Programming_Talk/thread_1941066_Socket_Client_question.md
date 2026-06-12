---
title: "Socket: Client question"
date: 2012-03-14
forum: Programming Talk
---

### Post by geewhan on 2012-03-14
Hello,

I am trying to write a client code in C. What I would like to do is create like an Instant message server-client socket. Where I want to have one Server and multiple Clients. I come to a problem that the client may not handle this, but this cannot be true since we do have instant message. I say this because the SocketDiagram.png I have attached shows that data needs to be send first then receive. 

So I present the problem what if you have 1 Server and 3 Clients.

   If one Client writes/sends (lets say "Hello"), then how would the other two Clients receive/read that data (saying "Hello) if Clients writes/sends first. Unless the server is involve with this problem. I hope that makes sense.

I have attached the 1 Server and 3 Clients png and SocketDiagram png, as well as, the server code.

Thanks for your time

```

/* This is a server. This code allows multiple client
to connect with the same server's port. 
Non-Blocking I/O and select(); 

Step 1: Setup Address structure
Step 2: Create a socket
Step 3: Bind the socket to the port
Step 4: Listen to the socket
Step 5: Setup an infinite loop to make connections

IBM
http://publib.boulder.ibm.com/infocenter/iseries/v5r3/
index.jsp?topic=%2Frzab6%2Frzab6xnonblock.htm   
*/
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <unistd.h>
#include <sys/types.h> 
#include <sys/socket.h>
#include <netinet/in.h>

#include <arpa/inet.h>
#include <netdb.h>

#define MAX_CLIENTS 20

void error(const char *msg)
{
	perror(msg);
	exit(1);
}

int main(int argc, char *argv[])
{
	fd_set master;    //file descriptor master list
	fd_set read_fds;  //file descriptor temp list for select()
	int fdmax;        //file descriptor maximum number

	int sockfd, newsockfd, portno;//socket, accept, port number
	socklen_t clilen;
	char buffer[256];//for recv and send of data
	int yes=1; //for setsockopt
	struct sockaddr_in serv_addr, cli_addr;
     	struct client{                          //struct used to store client information
          char name[32];                     //contains the client name
          int  fd;                           //contains the client file descriptor
     	};
     	struct client database[MAX_CLIENTS];    //database of client information
     	memset(&database, 0, sizeof database);
     	int numClients = 0;                     //keep track of how many clients are connected
	int i, j; //loop counters
	int nbytes; //data recv from the client
	char remoteIP[INET6_ADDRSTRLEN + 1];

	FD_ZERO(&master);    // clear the master and temp sets
	FD_ZERO(&read_fds);

	//Check if port is given
	if (argc < 2) {
		fprintf(stderr,"ERROR, no port provided\n");
		exit(1);
	}

	//Step 1: Setup Address structure
	bzero((char *) &serv_addr, sizeof(serv_addr));
	portno = atoi(argv[1]);
	serv_addr.sin_family = AF_INET;
	serv_addr.sin_addr.s_addr = INADDR_ANY;
	serv_addr.sin_port = htons(portno);


	//Step 2: Create a socket
	sockfd = socket(AF_INET, SOCK_STREAM, 0);
	if (sockfd < 0){
		error("ERROR opening socket");
	}
	printf("The sockfd1 value is: %d\n", sockfd);
		
	//reuse port if it was still in use
	if (setsockopt(sockfd,SOL_SOCKET,SO_REUSEADDR,
			&yes,sizeof(int)) == -1) {
		error("setsockopt");
		exit(1);
	}

	//Step 3: Bind the socket to the port
	if (bind(sockfd, (struct sockaddr *) &serv_addr,
			sizeof(serv_addr)) < 0){
		close(sockfd);
	}


	//Step 4:Listen to the socket
	if (listen(sockfd,10) == -1){
		error("ERROR on listen");
		exit(3);
	}

	//add file descriptor to master set list
	FD_SET(sockfd, &master);
	fdmax = sockfd; //as of now, the biggest fd is listener
	printf("The fdmax value is: %d\n", fdmax);
     	printf("Waiting for Client connections...\n");
     	usleep(1000);	
	//main while loop: LOOP and check for connection requests, recieved messages
	while(1) {
		read_fds = master; //copy master list to temp list

		//Check to see if the select call failed.
		if (select(fdmax+1, &read_fds, NULL, NULL, NULL) == -1) {
			perror("select");
			exit(4);
		}
		//printf("We are at before the main for loop");
		printf("The sockfd2 value is: %d\n", sockfd);
		
		//Step 5: Setup an infinite loop to make connections
		for(i = 0; i <= fdmax; i++) {
			//Check to see if this descriptor is ready
			if (FD_ISSET(i, &read_fds)) { //Check if FD is set
				//Check to see if this is the listening socket 
				if (i == sockfd) {//the fd is the listener port [a client is attempting to connect()]
					//handle new connections
					clilen = sizeof(cli_addr);
					newsockfd = accept(sockfd, 
							(struct sockaddr *) &cli_addr, 
							&clilen);
					printf("The newsockfd value is: %d\n", newsockfd);
					if (newsockfd < 0) 
						error("ERROR on accept");
					else {//accept successful
						//Add the new incoming connection to the master read set                          
						FD_SET(newsockfd, &master); //add fd to master list
						if (newsockfd > fdmax) {    //keep tracks of the FD max
							fdmax = newsockfd;
                                   			database[numClients].fd = newsockfd; //add connection to array
                                   			numClients++; //increment # of client connections
                                   			printf("New Connection Accepted - Total Connections: %d\n", numClients);
						}
						printf("selectserver: new connection from %s on "
								"socket %d\n",
								inet_ntop(AF_INET, &(cli_addr.sin_addr),
								remoteIP, sizeof(remoteIP)),
								newsockfd);
					}
				} else {//not from listener port, must be data from client
					// handle data from a client
					printf("  Descriptor %d is readable\n", i);
					if ((nbytes = recv(i, buffer, sizeof buffer, 0)) <= 0) {
						//Checks if any client(s) closed
						if (nbytes == 0) {//conection closed
							printf("Alert: socket %d hung up\n", i);
						} else {
							error("recv");
						}
						close(i); //close sockfd that leaves!
						FD_CLR(i, &master); //remove that client from master set
					} else {
						//we got some data from a client
						for(j = 0; j <= fdmax; j++) {
							//send to data every client 
							if (FD_ISSET(j, &master)) {
								//except the client that sent the data
								if (j != sockfd && j != i) {
									if (send(j, buffer, nbytes, 0) == -1) {
										error("send");
									}
								}
							}
						}
					}
				} // End handle data from client
			} // End got new incoming connection
		} // End flag set by a file descriptors
	} // End of main while Loop

	return 0;

}//End of main 



```

---

### Post by geewhan on 2012-03-14
Also when I get a chance to log on my Linux, I will print screen running code of the terminal to show what I mean, if no one understands my problem. If you run the server code I have posted and run telnet, that is what I want. If I run a simple client code such as the one below it will wait. I understand that fgets() will make the client wait, but I do not think that will fix the problem.

Thanks

```
#include <stdio.h>
#include <stdlib.h>
#include <unistd.h>
#include <string.h>
#include <sys/types.h>
#include <sys/socket.h>
#include <netinet/in.h>
#include <netdb.h> 

void error(const char *msg)
{
    perror(msg);
    exit(0);
}

int main(int argc, char *argv[])
{
    int sockfd, portno, n;
    struct sockaddr_in serv_addr;
    struct hostent *server;

    char buffer[256];
    if (argc < 3) {
       fprintf(stderr,"usage %s hostname port\n", argv[0]);
       exit(0);
    }
    portno = atoi(argv[2]);
    sockfd = socket(AF_INET, SOCK_STREAM, 0);
    if (sockfd < 0) 
        error("ERROR opening socket");
    server = gethostbyname(argv[1]);
    if (server == NULL) {
        fprintf(stderr,"ERROR, no such host\n");
        exit(0);
    }
    bzero((char *) &serv_addr, sizeof(serv_addr));
    serv_addr.sin_family = AF_INET;
    bcopy((char *)server->h_addr, 
         (char *)&serv_addr.sin_addr.s_addr,
         server->h_length);
    serv_addr.sin_port = htons(portno);
    if (connect(sockfd,(struct sockaddr *) &serv_addr,sizeof(serv_addr)) < 0) 
        error("ERROR connecting");
    printf("Please enter the message: ");
	while(1){//Edited While Loop
		bzero(buffer,256);
		fgets(buffer,255,stdin);
		n = write(sockfd,buffer,strlen(buffer));
		if (n < 0) 
			error("ERROR writing to socket");
		bzero(buffer,256);
		n = read(sockfd,buffer,255);
		if (n < 0) 
			error("ERROR reading from socket");
		printf("%s\n",buffer);
	}//Edited: While Loop
    close(sockfd);
    return 0;
}

```

---

### Post by dwhitney67 on 2012-03-15
fgets() will indeed block, thus preventing your client application from asynchronously handling reception of data from the socket.

The simple solution that I can suggest is that you consider multi-threading.  Here's a very basic example, which lacks a lot of error checking, and for which I have NOT tested:
```

#include <sys/socket.h>
#include <arpa/inet.h>
#include <string.h>
#include <stdlib.h>
#include <sys/select.h>
#include <pthread.h>
#include <stdio.h>

void error(const char *msg)
{
    perror(msg);
    exit(-1);
}

void* receiver(void* arg);
void* sender(void* arg);

int main(int argc, char** argv)
{
    unsigned short port = 9000;
    const char*    host = "localhost";
    int            sock = socket(AF_INET, SOCK_STREAM, 0);

    // old-school method; use getaddrinfo() instead.
    struct sockaddr_in sin;
    memset(&sin, 0, sizeof(sin));
    sin.sin_family      = AF_INET;
    sin.sin_port        = htons(port);
    sin.sin_addr.s_addr = inet_addr(host);

    
    if (connect(sock, (struct sockaddr*) &sin, sizeof(sin)) != 0)
    {
        error("Error connecting to server.");
    }

    pthread_t recv_tid, send_tid;

    pthread_create(&recv_tid, NULL, receiver, &sock);
    pthread_create(&send_tid, NULL, sender, &sock);

    pthread_join(recv_tid, NULL);
    pthread_join(send_tid, NULL);

    return 0;
}

void* sender(void* arg)
{
    int sd = *(int*)(arg);
    int done = 0;

    while (!done)
    {
        char msg[80];

        printf("Enter message to send, or 'quit' to exit\n");
        fgets(msg, sizeof(msg), stdin);

        char* nl = strchr(msg, '\n');
        if (nl)
        {
            *nl = '\0';    // we don't want to send newline
        }

        if (strncmp(msg, "quit", 4) == 0)
        {
            done = 1;
        }
        else
        {
            send(sd, msg, strlen(msg), 0);
        }
    }

    return NULL;
}

void* receiver(void* arg)
{
    int sd = *(int*)(arg);

    fd_set save_set;
    FD_ZERO(&save_set);
    FD_SET(sd, &save_set);

    int done = 0;

    while (!done)
    {
        fd_set read_set = save_set;

        int sel = select(sd + 1, &read_set, NULL, NULL, NULL);

        if (sel < 0)
        {
            error("Select failed.");
        }
        else if (sel > 0)
        {
            char msg[80] = {0};

            int bytes = recv(sd, msg, sizeof(msg) - 1, 0);

            if (bytes > 0)
            {
                msg[bytes] = '\0';
                printf("Received: %s\n", msg);
            }
            else
            {
                done = 1;    // server disconnected us?
            }
        }
    }

    return NULL;
}

```

P.S.  Why did you elect to use SOCK_STREAM (TCP) for a Chat application?  It seems to me that SOCK_DGRAM (UDP) would be more appropriate.

P.S. #2  Upon reflecting back on the code I presented above, I realized that accepting user input from standard-in and outputting received data to standard-out is probably not the best solution since output may intermix with the data being inputted.  Consider putting together a GUI (or use ncurses) where input and output can be handled in distinct areas of the GUI/screen.

---

### Post by geewhan on 2012-03-15
dwhitney,
 First, Thanks for helping me a lot.
To answer your question, does it really matter if I use TCP/UDP. I understand that UDP is unreliable and UDP is mostly use for graphic or video data package. The reason why it is unreliable the data may be sent not in numeric order. So this will not be great with sending the message since we would want them in order. I read this in a paper, but I may be wrong if so my mistake.

I have to say that you must be an advance programmer because I am seeing new commands today.
pthread, void* receiver(void* arg) I have never seen a function (void*) be a pointer, and this *(int*)(arg);
You do not have to explain what these does since I could google these.

Is there a way to give like a if condition where if the server is sending/writing the client is going to recv/read 
or is this not the best way of doing this.

Thanks again.

---

