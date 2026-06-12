---
title: "Sockets in C"
date: 2011-11-07
forum: Programming Talk
---

### Post by shashanksingh on 2011-11-07
I was trying out socket proramming in C, most of this code is from an online tutorial.

server.c
```

#include <sys/types.h>
#include <sys/socket.h>
#include <netinet/in.h>
#include <arpa/inet.h>
#include <stdio.h>
#include <stdlib.h>
#include <unistd.h>
#include <errno.h>
#include <string.h>


int main()
{
	int true=1;
	int master_socket=socket(AF_INET,SOCK_STREAM,0);
	struct sockaddr_in server_addr, client_addr;

	server_addr.sin_family = AF_INET;
	server_addr.sin_addr.s_addr = INADDR_ANY;
	server_addr.sin_port = htons(15000);
	bzero(&(server_addr.sin_zero),8);
	
	if (setsockopt(master_socket,SOL_SOCKET,SO_REUSEADDR,&true,sizeof(int)) == -1) 
	{
        perror("Setsockopt");
        exit(1);
    }
       
    if (bind(master_socket, (struct sockaddr *)&server_addr, sizeof(struct sockaddr))== -1) 
	{
        perror("Unable to bind");
        exit(1);
    }
    
    if (listen(master_socket,3)<0)
	{
		perror("listen");
		exit(0);
	}
    
	
	
	int connected;
	
	while(1);
	{
		connected = accept(master_socket, (struct sockaddr *)&client_addr,sizeof(struct sockaddr_in));

        printf("\n I got a connection from (%s , %d)",inet_ntoa(client_addr.sin_addr),ntohs(client_addr.sin_port));
		printf(" Listening \n");
		
	}
	
	return 0;
}


```

and my client.c

```

#include <sys/socket.h>
#include <sys/types.h>
#include <netinet/in.h>
#include <netdb.h>
#include <stdio.h>
#include <string.h>
#include <stdlib.h>
#include <unistd.h>
#include <errno.h>

int main()
{
	int client_socket=socket(AF_INET,SOCK_STREAM,0);
	struct sockaddr_in server_addr;
	struct hostent *host;
	
	host = gethostbyname("127.0.0.1");
	
	/* type of socket created in socket() */
	server_addr.sin_family = AF_INET;
	server_addr.sin_addr = *((struct in_addr *)host->h_addr);
	/* 7000 is the port to use for connections */
	server_addr.sin_port = htons(15000);
	bzero(&(server_addr.sin_zero),8);
			
	if (connect(client_socket, (struct sockaddr *)&server_addr, sizeof(struct sockaddr))== -1) 
		puts("error connecting..");
	  
	return 0;
}


```

The problem is when I run the client program, it doesnt throw any errors, just terminates.
But the server doesn't tell me it got a connection..

The actual code was quite lengthy, I thought this should be enough to make a simple connection

---

### Post by 11jmb on 2011-11-08
That code didn't work for me either. Why not try writing your own? That way you can learn as you go and come back here if you don;t understand something.

---

### Post by 11jmb on 2011-11-08
Also, try removing the accept from the while loop. I haven't don networking in C for a long time, but I thought an accept() call was a one-time thing per connection.

---

### Post by gnometorule on 2011-11-08
So what does your server do precisely? Please describe. Does it print anything, loop eternally, or exit with/without error?

There are a number of issues I noticed upon browsing, and probably others I didn't see on first read:

(1) the host you use gethostbyname() on is "lo", 127.0.0.1 is its address.

(2) use htonl() on addr_any as well

You should also always check and process success in socket API calls, which you don't for the accept() call.

---

### Post by gnometorule on 2011-11-08
The accept() in a loop, if all else is working ok, should be fine as the proper socket option is being set. I think.

---

### Post by 11jmb on 2011-11-08
> **gnometorule said:**
> The accept() in a loop, if all else is working ok, should be fine as the proper socket option is being set. I think.

Yes but there is not reason to be doing that.

The reason this code is not working is the semicolon after the wile statement, though.

---

### Post by shashanksingh on 2011-11-08
Ok, as per the suggestions, I removed the loop just in case, wrote my own code from scratch..
This one should be simpler to debug..

All My server is trying to do is get a connection and print the new connection's socket descriptor

The client simply tries to connect
(Hello World Of sockets :P)

Server.c:
```

#include <stdio.h>
#include <stdlib.h>

//For network Functions

#include <sys/socket.h>
#include <sys/types.h>
#include <netinet/in.h>

int main()
{
	//create a master socket
	
	int master_socket= socket(AF_INET, SOCK_STREAM, 0);
	if(master_socket==-1)
	{
		perror("Couldn't create Socket");
		exit(1);
	}
	
	//create pan internet address structure
	struct sockaddr_in server_addr;
	
	//set the address and port
	server_addr.sin_family=AF_INET;
	server_addr.sin_addr.s_addr = INADDR_ANY;
	server_addr.sin_port= htons(15000);
	
	//bind the socket to the port
	if(bind(master_socket,(struct sockaddr *)&server_addr,sizeof(server_addr))==-1)
	{
		perror("Failed to Bind");
		exit(1);
	}
	
	//listen to a particular port
	if(listen(master_socket,5)==-1)
	{
		perror("Could not listen");
		exit(1);
	}
	
	printf("Waiting for Connections\n");
	int client_socket;
	struct sockaddr_in client_addr;
	
		client_socket=accept(master_socket, (struct sockaddr *)&client_addr, sizeof(client_addr));
		//if error print else print socket descriptor
		if(client_socket<0)
		{
			perror("Failed to connect");
			exit(1);
		}
		else
		{
			printf("Socket Descriptor is %d\n",client_socket);
		}
		
	return 0;
}


```


Client.c:

```

#include <stdio.h>
#include <stdlib.h>

//For network Functions

#include <sys/socket.h>
#include <sys/types.h>
#include <netinet/in.h>
#include <arpa/inet.h>

int main()
{
	//create client-side socket
	int client_socket= socket(AF_INET,SOCK_STREAM,0);
	
	//create server address
	struct sockaddr_in server_addr;
	
	//initialise server address
	server_addr.sin_family=AF_INET;
	server_addr.sin_addr.s_addr = inet_addr("127.0.0.1");
	server_addr.sin_port= htons(15000);
	
	if(connect(client_socket,(struct sockaddr *)&server_addr,sizeof(server_addr))<0)
	{
		perror("Error Connecting");
		exit(1);
	}
	
}


```


Now Here's what my server says on running:

Failed to connect: Bad address

and the client just executes itself and terminates, no errors.

I guess my error maybe somewhere here
server_addr.sin_addr.s_addr = inet_addr("127.0.0.1");

is this wrong? Since Im using both client and server on localhost, I thought setting the server address to 127.0.0.1 should do it.

---

### Post by shashanksingh on 2011-11-08
> **11jmb said:**
> Yes but there is not reason to be doing that.

The reason this code is not working is the semicolon after the wile statement, though.
Yeah, it was the semicolon. But could you please check the latest ones I have posted? I started from scratch and could learn a bit. Thanks. :-)

---

### Post by 11jmb on 2011-11-08
add something like the following before your final if/else:

```
printf("\n I got a connection from (%s , d)",inet_ntoa(client_addr.sin_addr),ntohs(client_addr.sin_port));
```

and post the output

---

### Post by shashanksingh on 2011-11-08
I thik I just got the error.

In the accept() function in the server, apparently the last parameter is an address of an integer which gives the size of the client address.

I used sizeof directly in the above code, which gave an integer, but then I passed the address of that integer. Seems to be working now.

---

### Post by emiller12345 on 2011-11-08
I would start my checking each program independently by using netcat to test them.  That will at least break the problem into two more manageable parts.

---

### Post by shashanksingh on 2011-11-08
> **emiller12345 said:**
> I would start my checking each program independently by using netcat to test them.  That will at least break the problem into two more manageable parts.
Is it similar to netstat?

---

### Post by emiller12345 on 2011-11-08
no not really. netcat is a simple program that opens a network connection.  it can act as a server or a client.  a real simple example is...on one computer (the server) run ...```
echo 'hello world!' | /bin/nc.openbsd -l 8080
```and on another computer (the client) run...```
/bin/nc.openbsd 127.0.0.1 8080
```but replace the ip address with that of the server. you should see on the client...```
hello world!
```8080 is the tcp port number
you can also send data from the client by 
```
echo 'greets' | /bin/nc.traditional 127.0.0.1 8080
```

---

### Post by emiller12345 on 2011-11-08
you can also save the individual packets on the wire with the command
```
sudo tcpdump -i any -s 0 -n -vv -w ~/Desktop/mypcap.pcap
```
and you can view the saved data with wireshark (needs to be installed separately, in the repos)
```
wireshark ~/Desktop/mypcap.pcap
```

---

