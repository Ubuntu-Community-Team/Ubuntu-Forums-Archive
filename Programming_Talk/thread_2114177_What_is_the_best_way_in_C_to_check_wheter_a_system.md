---
title: "What is the best way in C to check wheter a system is up"
date: 2013-02-09
forum: Programming Talk
---

### Post by stefangr1 on 2013-02-09
I'm making a daemon to control the lights in my living room. Based on the time of day it needs to adjust the light settings. Among other things, if the TV (which is on the network) is on I wan't more cosy light settings. I'm programming everyting in C.

My question: what is the best way to check whether another system is up?

I could use system() to do a ping, and capture the return data in a buffer, but that seems sloppy. Are there any simple ICMP (or ARP?) implementations that are easy to include in a program?

---

### Post by r-senior on 2013-02-09
Could you try to open a socket connection to a port that you know is open and act upon the return value from connect()?

---

### Post by stefangr1 on 2013-02-09
> **r-senior said:**
> Could you try to open a socket connection to a port that you know is open and act upon the return value from connect()?

Great idea, thank you. This way it's much more elegant and efficient than turning the program into some kind of script that executes all sorts of other programs.

I've now made it like this (in case it might be helpful for others):

```
#include <stdlib.h>
#include <stdio.h>
#include <string.h>
#include <sys/socket.h> 
#include <arpa/inet.h>
#include <unistd.h>

#define PORT_NR 80
#define ERROR -1
#define IP "192.168.1.12"

int main(int argc, char *argv[])
{
    int sockfd, len, result;
    struct sockaddr_in address;
    
    time_t t;
    struct tm *tstruct;
    
    // Create a socket
    sockfd = socket(AF_INET, SOCK_STREAM, 0);
    
    // Set a timeout interval
    struct timeval tv;
    tv.tv_sec = 2;  // 2 Seconds timeout	
    setsockopt(sockfd, SOL_SOCKET, SO_RCVTIMEO,(struct timeval *)&tv,sizeof(struct timeval));	
	
    // Name the socket
    address.sin_family = AF_INET;
    address.sin_addr.s_addr = inet_addr(IP);
    address.sin_port = htons(PORT_NR);
    len = sizeof(address);
    
    // Check whether a connection is possible
    result = connect(sockfd, (struct sockaddr *)&address, len);
    if(result == ERROR)
    { 
	printf("Could not connect!\n");
	return ERROR;
    }
    printf("System is up!\n");
    close(sockfd);
    return 0;
}
```

---

