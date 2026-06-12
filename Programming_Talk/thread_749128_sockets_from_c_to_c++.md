---
title: "sockets: from c to c++"
date: 2008-04-08
forum: Programming Talk
---

### Post by careca on 2008-04-08
Hi, I'm having problem with compiling c code with g++. I'm doing this because I want to write a little program in C++ from an example in C.
In particular, the
inet_addr
function is not found when I compile with g++.
How can I resolve? Libraries should not be the same in C and C++ for sockets?

---

### Post by heikaman on 2008-04-08
use inet_aton  instead of inet_addr it's better, man inet_aton.

and can you post the complete example ?

---

### Post by careca on 2008-04-08
This is my main.cpp

```
#include <iostream>
#include <string>
#include <sys/types.h> 
#include <sys/socket.h> 
#include <netinet/in.h> 
#include <fcntl.h>
#include <fstream>

//#include <arpa/inet.h>
//#include <stdio.h> 
using namespace std;

int main(int argc, char** argv)
{
	// Local variables
	int aPortIn = 5000;
	int aPortOut = 5001;
	int sockfd;
	struct sockaddr_in aLocal;
	struct sockaddr_in *aRemotes;
	string aPathFile = "/home/Andrés/Desktop/ConfFile";
	string aPathTextFile = "/home/Andrés/Desktop/TextFile";
	string aBuffer = "";
	string aIPtemp;
	string *aIPs;
	int aN;
	int aNtemp;
	int aIndex;

	// Check argument is IP
	if (argc != 2)
	{

		fprintf(stderr, "Usage: Local %s IP address\n", argv[0]);
		exit(1);
	}
	
	// Create socket
	if ((sockfd = socket(AF_INET, SOCK_STREAM, 0)) < 0)
	{ 
		perror(NULL);
		exit(2);
	}

	aLocal.sin_family = AF_INET;
	aLocal.sin_addr.s_addr = inet_addr(argv[1]);
	aLocal.sin_port = htons(aPortOut);

	// Binding
	int e = bind( sockfd, (struct sockaddr *)&aLocal, sizeof(aLocal));
	cout << argv[1]<<"   !\n"<< e <<"   \n";
	if(bind( sockfd, (struct sockaddr *)&aLocal, sizeof(aLocal) ) < 0)
	{	
		perror(NULL);
		close(sockfd);cout << argv[1]<<"!\n";
		exit(3);
	}
	
	// Load nodes
	ifstream aFile;
	aFile.open(aPathFile.c_str(), ios::in);
	if(!aFile)	{	cout << "The CONF FILE is missing!\n";	exit(3);	}

	aFile >> aN;
	aIPs = new string[aN];
	aRemotes = new sockaddr_in[aN];

	aIndex = 0;
	while( !aFile.eof() && aIndex < aN )
	{
		aFile >> aIPs[aIndex];
		cout << aIPs[aIndex] << "\n";
		aRemotes[aIndex].sin_family = AF_INET;
		aRemotes[aIndex].sin_addr.s_addr = inet_addr(aIPs[aIndex].c_str());
		aRemotes[aIndex].sin_port = htons(aPortIn);		
		aIndex++;
	}
	
	aFile.close();
	
	// Load File
	fstream aTextFile;
	aTextFile.open(aPathTextFile.c_str(), ios::in|ios::out);
	if(!aTextFile)	{	cout << "The TEXT FILE is missing!\n";	exit(3);	}
	while( !aTextFile.eof() )
	{
		//aTextFile >> aTemp;
		//aBuffer.append(aTemp);
	}
	
	// Creating connection
	if( listen(sockfd, aN) < 0)
	{
		perror(NULL);
		close(sockfd);
		exit(3);
	}
	
	
	/* Initialization: How to
	 * Fork n times
	 * Create link, send ok
	 * Children die
	 * Parent recreate link to go on
	 */
	
	/* How link will be:
	 * Server-Client for every node
	 * One port for outgoing calls
	 * one for incoming
	 * Nodes will be identified by id in the messages
	 */
	
	// CreateInitialLink() <-
	// Define: address of *NumberOfNodes, *NumberOfNodesUpToNow
	// *sockaddr_in
	
	

	aTextFile.close();
	close(sockfd);
	
	return 0;
}

```

I'm working on it. I solved this problem by including
<arpa/inet.h>
but, i don't want to include it, because I want to do like my professor does.

---

### Post by heikaman on 2008-04-08
> **careca said:**
> 
I'm working on it. I solved this problem by including
<arpa/inet.h>
but, i don't want to include it, because I want to do like my professor does.


inet_addr and inet_aton are both defined in <arpa/inet.h> so you have to include it, maybe your professor forgot to include it :)

and inet_aton is better, because inet_addr returns -1 on error which is a valid address "255.255.255.255".
read man inet_aton.

---

### Post by careca on 2008-04-08
Here is my professors
datagram_sender.c
He compiles it with gcc, and works (I mean, there is no arpa library, and it inet_addr() and bind() correctly)
```
#include <stdio.h> 
#include <sys/types.h> 
#include <sys/socket.h> 
#include <netinet/in.h> 
#include <fcntl.h> 

#define SIZE 1400 
char buf[SIZE]; 

#define RECV_PORT 5000 
#define SENDER_PORT 5001 

int main(int argc, char *argv[]) { 

  int sockfd; int nread; 
  struct sockaddr_in remote_addr, local_addr; 
  int len; 
  
  if (argc != 2) { 
    fprintf(stderr, "Usage: %s IPaddr\n", argv[0]); 
    exit(1); 
  } 
  
  if ((sockfd = socket(AF_INET, SOCK_DGRAM, 0)) < 0) { 
    perror(NULL); 
    exit(2); 
  } 

  local_addr.sin_family = AF_INET; 
  local_addr.sin_addr.s_addr = htonl(INADDR_ANY); 
  local_addr.sin_port = htons(SENDER_PORT); 

  remote_addr.sin_family = AF_INET; 
  remote_addr.sin_addr.s_addr = inet_addr(argv[1]); 
  remote_addr.sin_port = htons(RECV_PORT); 

  if (bind(sockfd, (struct sockaddr *)&local_addr, sizeof(local_addr)) < 0) { 
    perror(NULL); 
    close(sockfd); 
    exit(3); 
  } 
  
  len = sizeof(remote_addr); 
  sendto(sockfd, "Hi", 2, 0, (struct sockaddr *)&remote_addr, len); 
  printf (" I sent a message...\n");
  nread = recvfrom(sockfd, buf, SIZE, 0, (struct sockaddr *)&local_addr, &len); 
  printf (" I got back %s\n", buf);
  close(sockfd); 
  exit(0); 
}
```

---

