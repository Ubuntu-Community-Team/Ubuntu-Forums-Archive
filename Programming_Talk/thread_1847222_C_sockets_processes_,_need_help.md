---
title: "C sockets processes , need help"
date: 2011-09-20
forum: Programming Talk
---

### Post by cap10Ibraim on 2011-09-20
):P okay I just need to know if my code is clean ,  does it generate zombie processes , is the signal handling correct 
I was reading Beej's Guide for Network programming , this is just the client side
```

#include <stdio.h>
#include <stdlib.h>
#include <unistd.h>
#include <errno.h>
#include <string.h>
#include <sys/types.h>
#include <sys/socket.h>
#include <netinet/in.h>
#include <arpa/inet.h>
#include <netdb.h>
#include <sys/wait.h>
#include <signal.h>
#define SERVER_PORT  "4950"
#define MAX_LENGTH 100
void sigchld_handler(int s)
{
	while(waitpid(-1,NULL,WNOHANG)>0);
}
int sendDatagramSocket(char *,char *,char *);
int sendStreamSocket(char *,char *,char *);
int main(int argc ,char *argv[])
{
	int choose,quit=0,status,temp;
	char buff[MAX_LENGTH];
	struct sigaction sa;
	sa.sa_handler=sigchld_handler;
	sigemptyset(&sa.sa_mask);
	sa.sa_flags=SA_RESTART;
	if(sigaction(SIGCHLD,&sa,NULL)==-1) {
		perror("sigaction");
		return 1;
	}
	while(1) {
		printf("\n*********************MAIN MENU**********************\nEnter 1 to send a message\nEnter 2 To Quit :");
		scanf("%d",&choose);
		switch(choose){
			case 1:
				printf("\n*********************SUB MENU**********************\nEnter your message ");
				scanf("%d",&temp);
				fgets(buff,MAX_LENGTH,stdin);
				printf("Your Message %s",buff);			
				printf("\nType 1: to send DGRAM\nType 2: to send STREAMSOCK\nAnything else to go back: ");
				scanf("%d",&temp);
				switch(temp){
					case 1:
						if(!fork()) {
							//printf("\nthis is the child");
							int t=sendDatagramSocket(argv[1],SERVER_PORT,buff);
							//printf("\nt=%d",t);
							if(t==0) exit(EXIT_SUCCESS);
						}
						break;
					case 2:
						//
						break;
					default:
						break;
				}
				break;
			case 2:
				quit=1;
				break;
			default: 
				break;
		}
		if(quit==1)
			return 0;
	}
	return 0;
}

int sendDatagramSocket(char *destination,char *port, char *message)
{
	int sockfd,rv;
	struct addrinfo hints,*servinfo,*p;
	int numbytes;
	memset(&hints,0,sizeof hints);
	hints.ai_family=AF_UNSPEC;
	hints.ai_socktype=SOCK_DGRAM;
	if((rv = getaddrinfo(destination, port, &hints, &servinfo))!=0){
		fprintf(stderr,"getaddrinfo: %s\n",gai_strerror(rv));
		return 1;
	}
	for(p=servinfo;p!=NULL;p=p->ai_next){
		if((sockfd=socket(p->ai_family,p->ai_socktype,p->ai_protocol))==-1){
			perror("talker2:socket");
			continue;
		}
		break;
	}
	if(p==NULL){
		fprintf(stderr,"talker: failed to bind socket\n");
		return 2;
	}
	if((numbytes=sendto(sockfd,message,strlen(message),0,p->ai_addr,p->ai_addrlen))==-1){
		perror("talker: sendto");
		return 3;
	}
	freeaddrinfo(servinfo);
	//printf("talker: sent %d bytes to %s\n", numbytes, destination);
    	close(sockfd);
    	return 0;
}

```

---

### Post by karlson on 2011-09-20
> **cap10Ibraim said:**
> ):P okay I just need to know if my code is clean ,  does it generate zombie processes , is the signal handling correct 

I have stupid question:

Why not just run and find out?

---

