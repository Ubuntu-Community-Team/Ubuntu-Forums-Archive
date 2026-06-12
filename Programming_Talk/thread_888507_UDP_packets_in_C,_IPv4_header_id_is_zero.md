---
title: "UDP packets in C, IPv4 header id is zero"
date: 2008-08-13
forum: Programming Talk
---

### Post by ChaoticMind on 2008-08-13
Hello, 

I wrote a program that exchanges UDP packets, but for some reason the Identification part of the IP header is always zero. The same code on windows (using winsock) would properly generate a random identification in the IP header. 
I believe that having an id for the IP packet is important in case fragmentation etc occurs. 

Note that the actual value for the identification part of the IP header was either tcpdump or wireshark. 
I will attach the stripped down (preliminary) version of both the client and the server.


Here is the client code: 
```

#include <stdio.h>
#include <sys/socket.h>
#include <netinet/in.h>
#include <stdlib.h>
#include <string.h>

int main(int argc, char *argv[]) {			// we will use the arguments in the next revision to specify amount of packets and how big they should be, destination IP and other similar parameters. 
	int socketDescriptor; 					// this will hold the socket info, ie it will represent our socket. 
	struct sockaddr_in serverAddress; 		// this will hold the server information, its IP, the port it should send to, address type, etc
	unsigned short int serverPort = 51234; 	// we're setting the port manually here. it's a variable because we want to change it later on through the parameters. we'll put here the default value. Note that we can use any of the unregistered ports (Ports 49,152 through 65,535)
	
	if ((socketDescriptor = socket(AF_INET, SOCK_DGRAM, 0)) < 0) {	// this line does two functions, it creates a socket of type AF_INET which is an internet address (as opposed to AF_UNIX which is a file pathname). Also, SOCK_DGRAM represents a UDP (connectionless) socket, as opposed to SOCK_STREAM which would be a TCP socket. The third argument is for special options which we don't need. This line also checks if socket returns -1 which would indicate that there was an error creating the socket. 
		printf("Could not create socket. \n"); 
		exit(1); // quits the program
	}
	serverAddress.sin_family = AF_INET; // sets the server address to type AF_INET, similar to the socket we will use. 
	serverAddress.sin_addr.s_addr = inet_addr("127.0.0.1"); // this sets the server address. 
	serverAddress.sin_port = serverPort;  // sets the server port. 
	
	char msg[] = "Hello World. ";  // For now, this is the message we will send. 
	printf("We will send the message: \"%s\" to the server. \n", msg); 
	
	if (sendto(socketDescriptor, msg, strlen(msg), 0, (struct sockaddr *) &serverAddress, sizeof(serverAddress)) < 0) { // We're sending over the socket described by socketDescriptor, and to the address described by serverAddress, the message held by 'msg'. sendto() returns -1 if it wasn't successful. Note that it doesn't return -1 if the connection couldn't be established (UDP)
		printf("Could not send data to the server. \n"); 
		exit(1); 
	}
	
	return 0; 
}

```

Here is the Server code:
```

#include <stdio.h>
#include <sys/socket.h>
#include <netinet/in.h>
#include <stdlib.h>
#include <string.h>

int main() {
	int socketDescriptor; 
	unsigned short int serverPort = 51234; 
	unsigned int msgSize = 100; // the max receivable size is msgSize. We should have this number larger than the max amount of data that we can receive. For now, this doesn't matter. 
	struct sockaddr_in serverAddress, clientAddress;  // we are going to store information for both the client and the server. 
	socklen_t clientAddressLength; 
	char msg[msgSize];  // msg received will be stored here. 
	
	socketDescriptor = socket(AF_INET, SOCK_DGRAM, 0); 
	
	// we fill the server information here. 
	serverAddress.sin_family = AF_INET; 
	serverAddress.sin_addr.s_addr = inet_addr("127.0.0.1");
	serverAddress.sin_port = serverPort; 
	
	if (bind(socketDescriptor, (struct sockaddr *) &serverAddress, sizeof(serverAddress)) < 0) { // we now have to bind the socket to the server descriptions stored in serverAddress. This will tell the socket on which port to listen on etc.. Again, bind returns -1 upon failure. 
		printf("Could not bind socket"); 
		exit(1); 
	}
	
	// now we wait for connections...
	listen(socketDescriptor, 2); // sets the queue size to two messages at a time. The number '2' was chosen arbitrarely. This line is optional. 
	printf("Waiting for data on UDP port %i\n", serverPort); 
	
	while(1) { // endless loop to keep on receiving data. 
		clientAddressLength = sizeof(clientAddress); 
		memset(msg, 0, msgSize);  // intialize msg to zero. 
		
		// now we receive the data, and check for errors. 
		if (recvfrom(socketDescriptor, msg, msgSize, 0, (struct sockaddr *)&clientAddress, &clientAddressLength) < 0) { // we now will wait to receive data on the socket described by socketDescriptor from a client. We also store this client information in clientAddress. This is useful if we want to reply to the client, or otherwise have information relating to where the received data initiated from. Again, the function recvfrom() returns -1 on error. 
			printf("An error occured while receiving data... Program is terminating. "); 
			exit(1); 
		}
		// we stored the information about the client in the strucct clientAddress. 
		printf("Received from %s on UDP port %d (port at sender is %d): \n%s\n", inet_ntoa(clientAddress.sin_addr), serverAddress.sin_port, ntohs(clientAddress.sin_port), msg); // note how we read the serverside port from serverAddress, and the client-side port from clientAddress, since it now holds information about the client, including which port it sent from. 
		
		
	} // end while 
	
	return 0; 
}

```

Is there something missing that I should do? Do i have to manually set the id? 
This is my first attempt at network programming, so I might be missing something basic..

---

### Post by dwhitney67 on 2008-08-13
> **ChaoticMind said:**
> Hello, 

I wrote a program that exchanges UDP packets, but for some reason the Identification part of the IP header is always zero. The same code on windows (using winsock) would properly generate a random identification in the IP header. 
I believe that having an id for the IP packet is important in case fragmentation etc occurs. 

Note that the actual value for the identification part of the IP header was either tcpdump or wireshark. 
I will attach the stripped down (preliminary) version of both the client and the server.

[snip code]

Is there something missing that I should do? Do i have to manually set the id? 
This is my first attempt at network programming, so I might be missing something basic..
I could not see within your code where you are checking for the ID.

When sending UDP messages, you will not have any fragmentation of messages, because the messages are guaranteed to be delivered whole.  There is also no guarantee as the order the messages are received in, and lastly there is no guarantee that you will even get a message that has been sent!

If you are looking for features that are not available to UDP, then I suggest you try using TCP for your protocol.

---

### Post by ChaoticMind on 2008-08-13
hello, thanks for the reply..

I'm not checking for the ID in the code itself, i used third party applications (tcpdump or wireshark)

I don't really mind about the lack of guarantees in my application, but surely there should still be a point of having a non-zero Identification for the IP? 
Is there a way to force one before sending the packet? can we modifiy the ip header? 
But shouldn't this be done by the OS on its own anyway? 

The only reason I can think of for this not being done automatically, is that there is no point for setting an identification number for the packet under UDP, yet windows still does set a number, any ideas?

Also, I thought fragmentation of messages would occur independently of the transport protocol? Isn't this true? And wouldn't this be a justification for the use of identification numbers?

---

### Post by dwhitney67 on 2008-08-13
Make Wikipedia your friend.  Here's a [description of UDP]("http://en.wikipedia.org/wiki/User_Datagram_Protocol"); pay close attention to the packet format.  I don't see where there is a field for an ID.

I think you really need to consider using [TCP]("http://en.wikipedia.org/wiki/Transmission_Control_Protocol") if you want your expectations met.

---

### Post by ChaoticMind on 2008-08-13
Whitney, I'm referring to the IP [ID field]("http://en.wikipedia.org/wiki/IPv4#Header"). I am aware that UDP doesn't have such a field, and that is not the issue.

To reiterate the problem, the UDP packet is being sent over IPv4, the identification section of the IP header is actually zero. As far as I know, this field is used in case there was fragmentation for the packet (which is done at the IP-level, not transport level. )

Shouldn't the kernel automatically assign id numbers for the packets? (and auto-increment for each subsequent packet)? Or should I manually do that? And if so, how do i do it? (I tried it on windows, and the id's were automatically assigned and incremented as expected)

---

### Post by dwhitney67 on 2008-08-13
Ah, you are referring to the IPv4 header, not the UDP header.  Try sending a larger message than "Hello World", perhaps a couple of kilobytes (if not more) of data to see if the fragmentation you desire occurs.

For a small message, as in your coding example, it would seem to reason that the ID will always be zero because the message was not fragmented.

---

### Post by ChaoticMind on 2008-08-13
Just to clarify, I don't really "desire" fragmentation, but I just want to make sure it works in case it does need to happen. (that's what the identification part of the IP header is used for, right?) 

I tried sending a big message on localhost, and for some reason, wireshark showed it all in one packet (even though it was larger than 1500 Bytes which is the MTU)

I guess I should try it over a network, but I don't have access to a second PC right now, i'll try it out later tonight.

---

