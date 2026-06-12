---
title: "Network Programming - NC Client Like Program"
date: 2007-11-28
forum: Programming Talk
---

### Post by Danikar on 2007-11-28
I used fgets in my C program to read from STDIN. Whenever it comes to that line it stops the program and waits for input.  Is there a way that I can set it up so that it only does this when there is something in STDIN for it to send.

The program basicly works like a client only form of netcat.

I am very noob to network programming that is why I am practicing with this type of program.

My program source is as below.

```

#include <stdio.h>
#include <netinet/in.h>

#define MAXLINE	255

int main(int argc, char *argv[])
{
	int socketfd, n, r;
	char buffer[MAXLINE + 1];
	struct sockaddr_in servaddr;

	// Exit if not 1 argument, IP
	if(argc != 3)
	{
		printf("Usage: %s IP_ADDRESS PORT\n", argv[0]);
		exit(-1);
	}

	// Creates socket and file descriptor, exit if error
	if( (socketfd = socket(AF_INET, SOCK_STREAM, 0)) < 0)
		printf("Socket Error\n");

	// Clear Struct for writing
	memset(&servaddr, '\0', sizeof(servaddr));

	// Set family and port
	servaddr.sin_family = AF_INET;
	servaddr.sin_port = htons(atoi(argv[2]));

	// Set Address
	if( inet_pton(AF_INET, argv[1], &servaddr.sin_addr) <= 0 )
		printf("inet_pton error for %s.", argv[1]);

	// Connect to server
	if( connect(socketfd, (struct sockaddr *) &servaddr, sizeof(servaddr)) < 0 )
	{
		printf("Could not connect\n");
		exit(-1);
	}

	printf("Type you request, then type . and return on a single");
	printf(" line to signify the end of your request.\n\n");
    
	printf("Enter data to send: \n");
	do
	{
		memset(&buffer, '\0', sizeof(buffer));
		fgets(buffer, MAXLINE, stdin);
		if(strcmp(buffer, ".\n") == 0)
			break;
		n = write(socketfd, buffer, MAXLINE);
	} while(n > 0);
	if(n < 0)
		printf("Error reading or writing to stream.\n");

	printf("Recieving Data... (Press CTRL-C to End Connection)\n");
	do
	{
		memset(&buffer, '\0', sizeof(buffer));
		n = read(socketfd, buffer, MAXLINE);
		fputs(buffer, stdout);    
	} while(n > 0);
	if(n < 0)
		printf("Error reading or writing to stream.\n");

	return 0;
}

```

---

### Post by dwhitney67 on 2007-11-28
The stdin you are using is a file descriptor; thus you can use it with a select() call.  When select() detects activity, you will be notified and you can do something similar to what you have now (i.e. capture stdin input and look for the single line with a dot).

Btw, select() will block unless you provide it a non-zero timeout period.  Thus without a timeout period, you are exactly where you are now.  Give a timeout period of say 1/4 of a second and your program will humm along nicely when there is no user input.

P.S.  I've had a few beers, thus don't blame me for inaccurate information.

---

### Post by Danikar on 2007-11-29
> **dwhitney67 said:**
> The stdin you are using is a file descriptor; thus you can use it with a select() call.  When select() detects activity, you will be notified and you can do something similar to what you have now (i.e. capture stdin input and look for the single line with a dot).

Btw, select() will block unless you provide it a non-zero timeout period.  Thus without a timeout period, you are exactly where you are now.  Give a timeout period of say 1/4 of a second and your program will humm along nicely when there is no user input.

**P.S.  I've had a few beers, thus don't blame me for inaccurate information.**

Thanks =) I'll play it like Vegas.  Always play the drunk guys numbers.

---

### Post by dwhitney67 on 2007-11-29
I'm not drunk yet... 8 x 6% is still the beginning for me.  But I'm lazy to verify what I have posted.

---

### Post by Danikar on 2007-11-29
Fair enough.

Does anyone know of a good guide that deals with the select() function specificly?

---

### Post by dwhitney67 on 2007-11-29
Guild?  Do you mean guide?  There's an example of the usage in the man-page.

```
$ man select
```

---

