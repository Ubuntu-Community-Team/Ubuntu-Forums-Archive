---
title: "UDP/TCP combination problem"
date: 2009-02-26
forum: Programming Talk
---

### Post by FaresH on 2009-02-26
Hi, 

I am trying to combine both TCP and UDP to create a reliable UDP server.
I know it has been done before, but I am trying to write it myself.

I am facing a problem I am not able to solve...

So I wrote a simple code that combines tcp and udp that is not related to my project, but has the same problem as in my project code.

The following code sends numbers between 0 and 9.
TCP socket sends the even numbers, 0 included.
UDP socket sends the odd numbers. 

_**Client side:**_

SYNOPSIS

./c <server address> <server port> <client port>

[PHP]
int main( int argc, char * argv[] ){
 
	int fd=0 ; 
	int mas_socket=0 ;
	int sla_socket=0 ;
	int client_socket=0 ; 
	int cur_received=0 ;
	int input = 99 ;

	u_int i=0 ;
	u_int maxdes=0 ;
	u_int sLen=0 ;
        u_int cLen=0 ;

	u_long offset=0 ; 
	u_long file_size=0 ; 

	char buf[BUFFSIZE] ;
	char * controler_array ; 

	struct sockaddr_in server ;
	struct sockaddr_in client ;	

	cLen = sizeof(client);
	sLen = sizeof(server); 

	server.sin_family = AF_INET;
        inet_aton(argv[1],&(server.sin_addr));
        server.sin_port = htons(atoi(argv[2]));

	client.sin_family = AF_INET;
        inet_aton(argv[1],&(client.sin_addr));
        client.sin_port = htons(atoi(argv[3]));

	printf("UDP: Server Socket\n");
	if( (sla_socket = socket (AF_INET,SOCK_DGRAM,0)) < 0 ){
		somethingIsWrong("UDP", SOCKERR);
	}

	printf("UDP: Client Socket\n");
	if( (client_socket = socket (AF_INET,SOCK_DGRAM,0)) < 0 ){
		somethingIsWrong("UDP", SOCKERR);
	}

	printf("UDP: Connect\n");
	if ((connect(sla_socket, (struct sockaddr*)&server, sizeof(server))) < 0 ){
		somethingIsWrong("UDP", CONCTERR);
	}

	printf("TCP: Connect\n"); 
	if( (mas_socket = tcp_connect(argv[1], atoi(argv[2]))) < 0 ){ 
		somethingIsWrong("TCP", SOCKERR); 
	}
	
	memcpy(buf, &input, sizeof(int));

	printf("UDP: sendto\n");
        if( sendto(sla_socket, buf, 1 ,0, (struct sockaddr *)&server, sLen) < 0 ){
		somethingIsWrong("UDP", SENDERR);
	}

	for( i=0 ; i < 10 ; i+=2 ){
		if( (cur_received= tcp_receive(mas_socket, buf, BUFFSIZE, 0 )) < 0 ){ 
			somethingIsWrong("TCP", READERR); 
		}
		printf("TCP- %i ", atoi(&buf[0]));
		i++;
		if( (cur_received = recvfrom(sla_socket, &buf, sizeof(buf),0, 
				(struct sockaddr *)&client, (socklen_t *) sizeof(client))) < 0 ){
			somethingIsWrong("UDP", READERR); 
		}
		printf("UDP- %i ", atoi(&buf[0]));
	}
	
	printf("\nMessage received\n");
}

[/PHP]

_**Server side:**_

SYNOPSIS

./s <server port> <client port>

[PHP]
int main( int argc, char * argv[] ){

	u_int output=0 ;
	u_int i=0 ;
	u_int cLen=0 ;

	char buf[BUFFSIZE] ;

	int cur_sent=0 ;
	int cur_recv=0 ;

	int client_tcp=0 ;
	int server_tcp=0 ;
	int server_udp=0 ;

        struct sockaddr_in server ;
	struct sockaddr_in client ;

	server.sin_family = AF_INET;
	server.sin_addr.s_addr = INADDR_ANY;
	server.sin_port = htons(atoi(argv[1]));

	client.sin_family = AF_INET;
	client.sin_addr.s_addr = INADDR_ANY;
	client.sin_port = htons(atoi(argv[2]));
	
	cLen = sizeof(client);

	printf("Udp: Socket\n");

	if( (server_udp = socket (AF_INET,SOCK_DGRAM,0)) < 0){
		somethingIsWrong("UDP", SOCKERR);
	}

	printf("Bind UDP\n");

	if(bind (server_udp, (struct sockaddr*)&server, sizeof(server))==-1){
		somethingIsWrong("UDP", BINDERR);
	}

	printf("Establish tcp server\n");

	if( (server_tcp = tcp_establish(atoi(argv[1]), BACKLOG )) < 0 ){
		somethingIsWrong("TCP", SOCKERR);
	}

	printf("New Client\n");

	if( (client_tcp = tcp_get_connection(server_tcp, NULL )) < 0 ){
		somethingIsWrong("TCP", ACCEPTERR);
	}

	if( (cur_sent = recvfrom(server_udp, &buf, sizeof(buf),0, (struct sockaddr *)&client, &cLen )) <= 0 ){
		somethingIsWrong("UDP", READERR); 
	}	

	memcpy(&output, buf, 1);

	printf("Received from udp client: %i\n", output);

	for( i=0 ; i < 10 ; i++ ){
		printf("%i ", i);
		memcpy(buf, &i, sizeof(u_int));
		if( tcp_send(client_tcp, buf, sizeof(u_int), 0) < 0 ){ 
			somethingIsWrong("TCP", SENDERR); 
		}
		i++;
		memcpy(buf, &i, sizeof(u_int));
		printf("%i ", i);
		if( sendto(server_udp, buf, BUFFSIZE, 0, (struct sockaddr *) &client, cLen ) < 0 ){ 
			somethingIsWrong("UDP", SENDERR); 
		}
	}	

	printf("\n");
}

[/PHP]

tcp_send: Sends data thru tcp socket.

tcp_receive: Receives data thru tcp socket.

tcp_establish: Establishes a tcp server by creating a new tcp socket, binds the socket, and listens. Used by server.

tcp_get_connection: Accepts new clients. Used by server

tcp_connect: Connects to a tcp server. Used by client.

somethingIsWrong: Receives a string, and a integer when an error occurs in one of the functions.

_**Problem: **_

This code compiles fine, I compiled it with -Wall. No errors or warnings.

When I run it I received the following:

_Server: _

bash-3.2$ ./s 5000 6000
Udp: Socket
Bind UDP
Establish tcp server
New Client
Received from udp client: 99
0 1 2 3 4 5 6 7 8 9 
End

_Client: _

bash-3.2$ ./c 127.0.0.1 5000 6000
UDP: Server Socket
UDP: Client Socket
UDP: Connect
TCP: Connect
UDP: sendto
UDP: Bad address
TCP- 0 
bash-3.2$ 

I am receiving a bad address on the udp socket. 
I know its a port problem. But why ? 

This is on Fedora since I am in the univ, but it gives me the same error at home when I compile and run it on ubuntu 7.0 .

---

### Post by dwhitney67 on 2009-02-26
It is very hard to follow your code because you have intermixed too many initializations with error checking, and many of the variables look very similar to each other.

Anyhow, one of the issues I saw in your code is that your client is using its 'sla_socket' (which is a UDP socket), and attempting to connect to the server.  UDP is connectionless!

Back to your code structure, consider taking the approach that if you cannot setup a socket, your program exits.  Then go with the approach of creating a library for all of your socket operations.

It would be easier if you wrote your app in an OOP language, but since you are using C, let's see if you can get something like the following setup for the Client:
```

int main()
{
  const char*          serverAddr = "127.0.0.1";
  const unsigned short serverPort = 50000;

  int udp_sd = CreateSocket(SOCK_DGRAM);
  int tcp_sd = CreateSocket(SOCK_STREAM);

  ConnectToServer(tcp_sd, serverAddress, serverPort);

  bool connected = true;

  fd_set savefds;
  FD_ZERO(&savefds);
  FD_SET(udp_sd, &savefds);
  FD_SET(tcp_sd, &savefds);

  while (connected)
  {
    fd_set readfds = savefds;
    int    max_sd  = (udp_sd > tcp_sd ? udp_sd : tcp_sd);
    int    sel     = select(max_sd + 1, &readfds, 0, 0, 0);

    if (sel <= 0) continue;

    // data needs to be read... verify from which source
    if (FD_ISSET(udp_sd, &readfds))
    {
       // receive from UDP port; then send data to TCP port

       ...
    }
    else if (FD_ISSET(tcp_sd, &readfds))
    {
      // receive from TCP port; then send data to UDP port

      // Note, if read fails from TCP port, assume server is
      // toast, and we are disconnected.

      ...

      if (bytesReadFromRecv == 0) connected = false;
    }
  }
}

```

The setup for your Server ought to be very similar.

Try to modularize your code so that it is not cluttered and replete with error checking.  Let me know if you have any more questions.  

P.S.  The notion of Client and Server are blurred in your applications because each application is serving both roles.

P.S.S.  The Server application needs to create the two sockets (as in the Client example), however for the TCP socket, it needs to bind the socket, listen on it, and then accept a connection from the Client.  Once the Client is connected, use the socket descriptor that is returned from accept() as your TCP handle to the Client.

---

### Post by FaresH on 2009-03-04
If an admin sees this thread, please be kind and delete it.

---

