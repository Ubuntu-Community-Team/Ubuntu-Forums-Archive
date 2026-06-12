---
title: "problem in socket programing"
date: 2006-11-26
forum: Programming Talk
---

### Post by drorl on 2006-11-26
hi all.
i'm trying to write a code for a client usuing tcp Protocol.
so far i went by online tutorials.
but i'm stuck at a point when i'm getting a compilation error which i don't understand.
here is the relevant code (the problematic line is marked):

#include <stdio.h>
#include <stdlib.h>
#include <unistd.h>
#include <errno.h>
#include <string.h>
#include <netdb.h>
#include <sys/types.h>
#include <netinet/in.h>
#include <sys/socket.h>


#define BUF_SIZE 256 //size of buffer that will be read writen at each time

void quit(FILE *src, int sockfd, int exitCode){
	fclose (src);
	shutdown(sockfd, SHUT_RDWR);
	close(sockfd);	
}

int main(int argc, char **argv){
	int sockfd, portNo, status, n;
	struct sockaddr_in server_addr;//this struct will hold the server details
	struct hostnet *hostInfo;//	
	char buffer[BUF_SIZE];//this buffer will hold data read from the source file
	FILE *src;

	if (argc < 3) {//incorrect input
    	fprintf(stderr,"usage  crftp server-port  server-hostname filename-to-transfer\n");
       	exit(1);
    }
	
	if ((hostInfo = gethostbyname(argv[2])) == NULL) {  // get the host info
		herror("error ,in translating the server name to IP adderess\n");
		exit(1);
    }
	
	if ((sockfd = socket(AF_INET, SOCK_STREAM, 0)) < 0) {
		perror("error in opening a client socket");
		exit (errno);
    }
	
	
	
	
	//initializing the struct that will hold the server details
	portNo = atoi(argv[1]);
	bzero((char *)&server_addr, sizeof(server_addr));
    server_addr.sin_family = AF_INET;
    server_addr.sin_port = htons(portNo);//converting from host byte order to network byte order
_**    memcpy(&server_addr.sin_addr.s_addr,hostInfo->h_addr_list[0], hostInfo->h_length);**_
	

and here is the compilation message:
tcpClient.c:44:Warning:assignment from incompatible pointer type
[B][U]tcpClient.c:62:error:dereferencing pointer to incomplete type
tcpClient.c:62:error:dereferencing pointer to incomplete type[/U][/B]

by the way if anyone knows why is the warning(it refferes the gethostbyname line) it will help too.

thanks a lot
dror](*,)

---

### Post by shining on 2006-11-26
```

struct hostnet *hostInfo;// 

```

hostnet or hostent ?

> 
struct hostent *gethostbyname(const char *name);


What is hostnet? If it didn't give you any errors, it means it exists?

---

### Post by drorl on 2006-11-26
thanks.
that was realy the problem.
the question is indeed what is hostnet and why did the compiler didn't say something about it?!:-k 
dror

---

