---
title: "[SOLVED] C, client/server: not transmitting or receiving message"
date: 2008-03-04
forum: Programming Talk
---

### Post by tehet on 2008-03-04
Hi,
I'm trying to send the message 'ping' or any other message of 4 chars or less from client.c to server.c. From examples I've found both the send()/recv() and the write()/read() functions but neither is working for me. How do I get server.c to read the message? Or is client.c not sending properly to begin with? If larger code snippets are needed please let me know.
Thanks.

client.c
```
	server_address.sin_family = AF_INET;
	server_address.sin_port = htons(server_port);
	server_address.sin_addr.s_addr = inet_addr(server_ip);
	memset(server_address.sin_zero, '\0', sizeof server_address.sin_zero);

	printf("Connecting to remote socket ... ");
	fflush(stdout);
	if ((connect(sockfd, (struct sockaddr *)&server_address, \
			sizeof server_address)) == -1) {
		perror("failed");
		exit(1);
	}
	else printf("succeeded.\n");

	//send(sockfd, message, 5, 0);
	write(sockfd, message, strlen(message));
```

server.c
```
	memset(message, '\0', sizeof message);
	while(1) {
		sin_size = sizeof remote_address;
		new_fd = accept(sockfd, (struct sockaddr *)&remote_address, &sin_size);
		sleep(1);

		//len = strlen(message);
		//recv(new_fd, message, len, 0);
		read(new_fd, message, strlen(message));
		printf("%s\n", message);
	}
```

Ps. I'll bet the while (1) sleep (1); is awefull but I think I need to read up on non-blocking reads(?) before I can fix that.

---

### Post by ruy_lopez on 2008-03-04
Test write()

```

if (write(sockfd, message, strlen(message)) < 0) {
        fprintf(stderr, "write error: %s\n", strerror(errno));
        exit(EXIT_FAILURE);
}

```

this'll tell you what's wrong. If you need help post the error here.

EDIT: do the same with read on the server.

---

### Post by tehet on 2008-03-04
Unfortunately it's not returning any errors on either the client or the server though I have errno.h included in both.

edit: I'm testing this all locally. Both the client and server run on 10.1.1.2. Perhaps that's significant.

---

### Post by ruy_lopez on 2008-03-04
Does it work without sleep()? Read usually blocks until it receives something. So you don't need to sleep(). If you want non-blocking use select().

---

### Post by tehet on 2008-03-04
> **ruy_lopez said:**
> Does it work without sleep()?
Hmm, nope.
> Read usually blocks until it receives something. So you don't need to sleep().
Without sleep I get 100% CPU load so I thought I throw in a quick and dirty sleep(). [Edit2: strike that. An earlier incarnation of my program did that, the current while() doesn't anymore]
> If you want non-blocking use select().
I'll look into that. Though from what I've [(not yet) read](http://www.kegel.com/c10k.html#top) that non-blocking stuff is going to be a lot of work (or at least take some time before I'll get it).

Edit: The server does receive something though. Each time I send something, the cursor of the server moves down, I think it's printing message ( == \0\0\0\0\0).

---

### Post by ruy_lopez on 2008-03-04
Post the code in its entirety, or attach a tarball, and I'll take a look at it. Sometimes silent errors creep in that affect the sending/receiving of data.

---

### Post by tehet on 2008-03-04
Thanks ruy_lopez, your help is much appreciated. I've cleaned it up a bit and here's the current form:
```
/*
	Socket exercise - Stream client
*/

#include <stdio.h> /* printf, scanf, etc */
#include <stdlib.h> /* ? */
#include <string.h> /* memset() */
#include <sys/types.h> /* socket(), connect(), etc */
#include <sys/socket.h> /* socket(), connect(), etc */
#include <netinet/in.h> /* inet_addr() */
#include <arpa/inet.h> /* inet_addr() */
#include <errno.h> /* perror() */

int main()
{
	int sockfd;
	struct sockaddr_in server_address;
	char server_ip[16];
	char message[5];
	unsigned short int server_port;

	memset(server_ip, '\0', sizeof server_ip);
	memset(message, '\0', sizeof message);
	printf("Enter server IP:\n");
	scanf("%15s", server_ip);			// fix me
	printf("Enter port number:\n");
	scanf("%hu", &server_port);			// fix me
	printf("Enter message:\n");
	scanf("%4s", message);				// fix me

	if ((sockfd = socket(PF_INET, SOCK_STREAM, 0)) == -1) {
		perror("Socket error: ");
		exit(EXIT_FAILURE);
	}
	server_address.sin_family = AF_INET;
	server_address.sin_port = htons(server_port);
	server_address.sin_addr.s_addr = inet_addr(server_ip);
	memset(server_address.sin_zero, '\0', sizeof server_address.sin_zero);
	if ((connect(sockfd, (struct sockaddr *)&server_address, \
			sizeof server_address)) == -1) {
		perror("Connection error: ");
		exit(EXIT_FAILURE);
	}
	if (send(sockfd, message, strlen(message), 0) == -1) {
		perror("Write error: ");
		exit(EXIT_FAILURE);
	}

	return 0;
}

```
```
/*
	Socket exercise - Stream server
*/

#include <stdio.h> /* printf, scanf, etc */
#include <stdlib.h> /* ? */
#include <string.h> /* memset() */
#include <sys/types.h> /* socket(), connect(), etc */
#include <sys/socket.h> /* socket(), connect(), etc */
#include <netinet/in.h> /* inet_addr() */
#include <arpa/inet.h> /* inet_addr() */
#include <errno.h> /* perror() */

#define PORT 9999
#define BACKLOG 10

int main()
{
	int sockfd, new_fd;
	struct sockaddr_in local_address;
	struct sockaddr_in remote_address;
	socklen_t sin_size;
	char message[5];

	if ((sockfd = socket(PF_INET, SOCK_STREAM, 0)) == -1) {
		perror("Socket error: ");
		exit(EXIT_FAILURE);
	}
	local_address.sin_family = AF_INET;
	local_address.sin_port = htons(PORT);
	local_address.sin_addr.s_addr = INADDR_ANY;
	memset(local_address.sin_zero, '\0', sizeof local_address.sin_zero);
	if ((bind(sockfd, (struct sockaddr *)&local_address, \
			sizeof local_address)) == -1) {
		perror("Socket error: ");
		exit(EXIT_FAILURE);
	}
	if ((listen(sockfd, BACKLOG)) == -1) {
		perror("Connection error: ");
		exit(EXIT_FAILURE);
	}

	memset(message, '\0', sizeof message);
	while(1) {
		sin_size = sizeof remote_address;
		new_fd = accept(sockfd, (struct sockaddr *)&remote_address, &sin_size);
		if (recv(new_fd, message, strlen(message), 0) == -1) {
			perror("Read error: ");
			exit(EXIT_FAILURE);
		}
		else printf("%s\n", message);
	}
	return 0;
}

```
I think the problem is with the server because telnetting to it gives the same result.

---

### Post by ruy_lopez on 2008-03-04
I couldn't get your code to show more than one char of message.

It'll be quicker if I show you how I do it. Then all you need to do is add the "scanf" to the client.c to make it do what you want.

The client takes the server's IP address from the command line. So run it like this: "./client 127.0.0.1"

client.c
```

#include <stdio.h>
#include <string.h>
#include <stdlib.h>
#include <errno.h>
#include <sys/socket.h>
#include <arpa/inet.h>

int main(int argc, char *argv[])
{
	int sockfd;
	struct sockaddr_in servaddr;
	char *string = "hello world"; // message

	if (argc != 2) {
		fprintf(stderr, "%s usage: <address>", argv[0]);
		exit(EXIT_FAILURE);
	}

	if ((sockfd = socket(AF_INET, SOCK_STREAM, 0)) < 0) {
		fprintf(stderr, "socket error: %s\n", strerror(errno));
		exit(EXIT_FAILURE);
	}

	memset(&servaddr, 0, sizeof(servaddr));
	servaddr.sin_family = AF_INET;
	servaddr.sin_port = htons(9999);

	if (inet_pton(AF_INET, argv[1], &servaddr.sin_addr) < 0) {
		fprintf(stderr, "inet_pton error: %s\n", strerror(errno));
		exit(EXIT_FAILURE);
	}

	if (connect(sockfd, (struct sockaddr *) &servaddr, 
						sizeof(servaddr)) < 0) {

		fprintf(stderr, "connect error: %s\n", strerror(errno));
		exit(EXIT_FAILURE);
	}

//	write(sockfd, string, strlen(string) + 1);	
	send(sockfd, string, strlen(string) + 1, 0);

	exit(0);
}

```

server.c
```

#include <stdio.h>
#include <string.h>
#include <stdlib.h>
#include <sys/socket.h>
#include <errno.h>
#include <arpa/inet.h>

#define LISTENQ 1024
#define BUFSIZE 1024

int main(int argc, char *argv[])
{
	int listenfd, connfd, on = 1;
	socklen_t clilen;
	struct sockaddr_in cliaddr, servaddr;
	char buf[BUFSIZE];

	if ((listenfd = socket(AF_INET, SOCK_STREAM, 0)) < 0) {
		fprintf(stderr, "socket error: %s\n", strerror(errno));
		exit(EXIT_FAILURE);
	}

	if (setsockopt(listenfd, SOL_SOCKET, SO_REUSEADDR, &on, 
							sizeof(on)) < 0) {
		fprintf(stderr, "setsockopt error: %s\n", strerror(errno));
		exit(EXIT_FAILURE);
	}

	bzero(&servaddr, sizeof(servaddr));
	servaddr.sin_family      = AF_INET;
	servaddr.sin_addr.s_addr = htonl(INADDR_ANY);
	servaddr.sin_port        = htons(9999);

	if (bind(listenfd, (struct sockaddr *) &servaddr, 
							sizeof(servaddr)) < 0) {
		fprintf(stderr, "bind error: %s\n", strerror(errno));
		exit(EXIT_FAILURE);
	}

	if (listen(listenfd, LISTENQ) < 0) {
		fprintf(stderr, "listen error: %s\n", strerror(errno));
		exit(EXIT_FAILURE);
	}

	for ( ; ; ) {
		clilen = sizeof(cliaddr);
		if ((connfd = accept(listenfd, (struct sockaddr *) &cliaddr, 
								&clilen)) < 0) {
			fprintf(stderr, "accept error; %s\n", strerror(errno));
			close(listenfd);
			exit(EXIT_FAILURE);
		}
		close(listenfd);
		break;
	}

//	read(connfd, buf, BUFSIZE);
	recv(connfd, buf, BUFSIZE, 0);
	printf("%s\n", buf);

	close(connfd);
	exit(EXIT_SUCCESS);
}

```

---

