---
title: "sockets: polling without select()"
date: 2008-04-18
forum: Programming Talk
---

### Post by careca on 2008-04-18
Hi people,
I'm trying to implement a distributed chat with sockets for learning purposes. I know TPC links are bidirectional but I want to do it this way:
-Each process is server/client in the same time
-Each process creates a link to the other (with streams, not datagram) for sending messages
-> so, in the same time, each process will receive a link request from each other process. The idea is to use tcp socket unidirectional.
-Each process enters a loop. In the loop the process tries to connect to the others, accept new requests, and send and receive data.
I don't want to use select() or similar, I just want to scan a table with known information (I know which port to look for others).
The number of processes are fixed.
I repeat, I'm doing this just to see if I can, I know there are more efficient methods.

I post the code I wrote. It has to be compiled and executed with a port number of this set: 6000, 7000, 8000, 9000. Excuse for the code, it is getting worse because I'm trying to find the problem.


```
#include <stdio.h> 
#include <sys/types.h> 
#include <sys/socket.h> 
#include <netinet/in.h> 
// Aggiunte queste inclusioni
#include <arpa/inet.h> //c++ socket
#include <stdlib.h> //c++ socket
#include <unistd.h> //c++ socket
#include <iostream>
using namespace std;
#include <fstream>

#define SIZE 1024 
char buf[SIZE]; 

//#define TIME_PORT 6000 
#define MAX_CONNECTIONS 4
#define NODES 2

struct Node {
	int Port;
	int SockR;
	int SockW;
	int SockR_stat;
	int SockW_stat;
	struct sockaddr_in R_struct;
	struct sockaddr_in W_struct;
	socklen_t R_socksize;
	socklen_t W_socksize;
};

int main(int argc, char *argv[]) {
	int sockfd, client_sockfd;
	int nread, len;
	struct sockaddr_in serv_addr, client_addr;
	time_t t;
	
	int *Node;
	int aLocalPort=0;
	int* aPorts;//[NODES] = {6000, 7000, 8000, 9000};//These will be loaded from file
	int* aSocks_Out;//[NODES] = {0, 0, 0, 0}; //These have to be allocated dinamically
	int* aSocksStatus_Out;
	int* aSocks_In;
	int* aSocksStatus_In;//[NODES] = {0, 0, 0, 0};//	"	"	"
	struct sockaddr_in* aAddress_Out;
	struct sockaddr_in* aAddress_In;
	struct sockaddr_in aTempAdd;
	int aI;
	char *aEndTemp;
	int aQuit=0;
	int aYes=1;
	socklen_t aAddressSize_In;
	socklen_t aAddressSize_Out;
	int aTemp;
	
	aPorts = new int[NODES];
	aSocks_Out = new int[NODES];
	aSocks_In = new int[NODES];
	aSocksStatus_In = new int[NODES];
	aSocksStatus_Out = new int[NODES];
	aAddress_Out = new sockaddr_in[NODES];
	aAddress_In = new sockaddr_in[NODES];
	
	aLocalPort = strtol ( argv[1], &aEndTemp, 0 );
	//aPorts[0] = strtol ( argv[1], &aEndTemp, 0 );
	aPorts[0] = 6000; aPorts[1] = 7000;
	aPorts[2] = 8000; aPorts[3] = 9000;
	for(aI=0;aI<NODES;aI++)
	{
		if(aPorts[aI] == aLocalPort)
		{
			aPorts[aI]=aPorts[0];
			aPorts[0]=aLocalPort;	
		}
	}
	

	/*if ( argc > 1 )
	{
		aLocalPort = strtol ( argv[1], &aEndTemp, 0 );
		if ( !(*aEndTemp == '\0') )
		{
				fprintf(stderr, "Error on port number:%s\n", argv[0]);
				exit(1);
		}
		else
		{	for(aI=0;aI<NODES;aI++)
			{	if(aPorts[aI]==aLocalPort)
				{	aLocalSocki=aI;	}
			}
		}
	}*/

	
	/* Create server-side socket */
	if((aSocks_Out[0] = socket(AF_INET, SOCK_STREAM, 0)) < 0)
	{	perror(NULL);	exit(2);	}
	if (setsockopt(aSocks_Out[0], SOL_SOCKET, SO_REUSEADDR, &aYes,
					sizeof(int)) == -1)
	{
		perror("setsockopt");
		exit(1);
	}
	/* Server-side sockets for incoming messages */
	for(aI=1;aI<NODES;aI++)
	{
		if ((aSocks_In[aI] = socket(AF_INET, SOCK_STREAM, 0)) < 0)
		{
			perror(NULL);
			exit(2);
		}
		else
		{
			cout<<aSocks_In[aI]<<" "<<htons(aPorts[aI])<<"\n";
			aAddress_In[aI].sin_family = AF_INET;
			aAddress_In[aI].sin_addr.s_addr = inet_addr("127.0.0.1");// htonl(INADDR_ANY);
			aAddress_In[aI].sin_port = htons(aPorts[aI]);
			aSocksStatus_In[aI]  = -1;
			aSocksStatus_Out[aI] = -1;
			aSocks_Out[aI] = -1;
		}
	}
	
	/* Bind address */
	aAddress_Out[0].sin_family = AF_INET;
	aAddress_Out[0].sin_addr.s_addr = inet_addr("127.0.0.1");//*/htonl(INADDR_ANY);
	aAddress_Out[0].sin_port = htons(aPorts[0]);
	if(bind(aSocks_Out[0], (struct sockaddr *)&aAddress_Out[0], sizeof(aAddress_Out[0])) < 0)
	{	perror(NULL);	exit(3);	}
	else
	{	cout<<"My IP is: "<<aAddress_Out[0].sin_addr.s_addr<<":"<<aAddress_Out[0].sin_port<<"\n";}
	
	
	/* Listen for incoming connections */
	if(listen(aSocks_Out[0], 5) < 0)
	{	perror("Error on listen()");	}
	for (;;)
	{
		//break;
		if(aQuit)
		{
			//Close all connections and quit
			cout << aQuit << "\n";
		}
		else
		{
			
			// i) Try to connect to all nodes
			for(aI=1; aI<NODES; aI++)
			{
				if(aSocksStatus_In[aI] < 0)
				{
					
					
					aAddressSize_In=sizeof(aAddress_In[aI]);
					aSocksStatus_In[aI] = connect(
												aSocks_In[aI],
												(struct sockaddr *) &(aAddress_In[aI]),
												sizeof(aAddress_In[aI])//aAddressSize_In
												);
					perror(NULL);
					cout<<sizeof(aAddress_In[aI])<<" size IN\n";
					if (setsockopt(aSocks_In[aI], SOL_SOCKET, SO_REUSEADDR, &aYes, sizeof(int)) == -1)
					{perror("setsockopt1");exit(1);}
					if(aSocksStatus_In[aI] < 0)
					{cout<<" Node "<<aI<<", "<<aAddress_In[aI].sin_addr.s_addr<<":"<<aAddress_In[aI].sin_port<<" seems to sleep.\n";}
					else
					{cout<<" Node "<<aI<<" found! "<<aAddress_In[aI].sin_addr.s_addr<<":"<<aAddress_In[aI].sin_port<<" -> S: "<< aSocksStatus_In[aI] <<" "<< aSocks_In[aI] <<"\n";}
				}
			}
			
			sleep(3);
			
			// ii) Accept non bloccante
			for(aI=1;aI<NODES;aI++)
			{
				if(aSocks_Out[aI] <= 0)
				{
					aAddressSize_Out=sizeof(aAddress_Out[aI]);
					aSocks_Out[aI] = accept(
											aSocks_Out[0],
											(struct sockaddr *) &(aAddress_Out[aI]),
											&(aAddressSize_Out)
											);		
					perror("accept");
					aTempAdd.sin_family		= aAddress_Out[aI].sin_family;
					aTempAdd.sin_addr.s_addr= aAddress_Out[aI].sin_addr.s_addr;
					aTempAdd.sin_port 		= aAddress_Out[aI].sin_port;
					cout<<aTempAdd.sin_family<<" "<<aTempAdd.sin_addr.s_addr<<" "<<aTempAdd.sin_port<<"\n";

					if (setsockopt(aSocks_Out[aI], SOL_SOCKET, SO_REUSEADDR, &aYes, sizeof(int)) == -1)
					{perror("setsockopt2");exit(1);}
					if(aSocks_Out[aI]>=0)
					{cout << " New node "<<aI<<" accepted. -> Descriptor: " << aSocks_Out[aI]<<"\n";}
					else
					{cout << " Error on "<<aI<<". -> S: " << aSocks_Out[aI]<<"\n";}
				}
			}

			// iii) Wait(2);
			sleep(3);
		}
				
		/* Transfer data */
		cout << " I try to send and receive time data\n";
		time(&t);
		sprintf(buf, "%s", asctime(localtime(&t)));
		//cout << buf;
		len = strlen(buf) + 1;
		for(aI=1; aI<NODES; aI++)
		{
			if(aSocks_Out >= 0)
			{
				write(aSocks_Out[aI], buf, len);
				perror(NULL);
				aTemp = shutdown(aSocks_Out[aI], SHUT_RDWR);perror(NULL);
				cout<<"!!!!!!!!!"<<aTemp<<"!!!!!!!!!\n";
			}
			aSocks_Out[aI] = -1;
		}
		
		for(aI=1; aI<NODES; aI++)
		{
			if(aSocks_In[aI] >= 0)
			{
				nread = read(aSocks_Out[aI], buf, len);
				printf ("Time at remote machine %d: d% is: %s", aI, aSocks_In[aI], buf);
				close(aSocks_In[aI]);
			}
			//aSocks_In[aI] = -1;
			aSocksStatus_In[aI] = -1;
		}
		sleep(5);
		//close(aSocks_Out[0]);
		//exit(0);
	}
}
```

My two questions are:
1) Is possible to do what I want?
2) Why my program fails?

Thank you for any suggestion.

---

### Post by dwhitney67 on 2008-04-18
Why don't you want to use select()?

Also, upon first examination of your code, I thought it was written in C... especially more so when I saw the include for stdio.h.  But it actually looks like you are attempting to write the code in C++.

Why don't try to create a class object that handles each port.  That way you reduce the redundancy in the code you have written thus far.

If you give up, you can peruse the code (see attachment) I wrote several years ago.

---

### Post by careca on 2008-04-24
Thank you.

I'm trying to write a sequential polling. I should know who is online, so is very easy (it should) to ask for everyone, and not just waiting.
I'm trying to write in c++, yes, I'm compiling with c++

---

