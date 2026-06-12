---
title: "download a file from a url in C++"
date: 2008-11-21
forum: Programming Talk
---

### Post by earobinson on 2008-11-21
Hey,

anyone have a really simple tutorial (at the socket level) about how to download a file (binary) in C++.

I really want to write a really simple wget function. I looked at the wget source code and there was way to much there. I just want a simple wget from a http website.

Cheers

---

### Post by rbprogrammer on 2008-11-21
> **earobinson said:**
> 
...
I looked at the wget source code and there was way to much there. 
...


Have you thought about taking the wget source and trimming it down to what you want?  When you say there is a way too much there, do you mean features?  Or too much code to understand what is going on within that code?

---

### Post by earobinson on 2008-11-21
> **rbprogrammer said:**
> Have you thought about taking the wget source and trimming it down to what you want?  When you say there is a way too much there, do you mean features?  Or too much code to understand what is going on within that code?
To much code to understand it all, I just want a simple tutorial, open the socked, grab the bin, save it to disk.

---

### Post by slavik on 2008-11-21
Here's a C version.

[php]
/*
 *      wget_sortof.c
 *
 *      Copyright 2007 Vyacheslav Goltser <slavikg@gmail.com>
 *
 *      This program is free software; you can redistribute it and/or modify
 *      it under the terms of the GNU General Public License as published by
 *      the Free Software Foundation; either version 2 of the License, or
 *      (at your option) any later version.
 *
 *      This program is distributed in the hope that it will be useful,
 *      but WITHOUT ANY WARRANTY; without even the implied warranty of
 *      MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
 *      GNU General Public License for more details.
 *
 *      You should have received a copy of the GNU General Public License
 *      along with this program; if not, write to the Free Software
 *      Foundation, Inc., 51 Franklin Street, Fifth Floor, Boston, MA 02110-1301, USA.
 */

/* get the main page from google.com */

#include <stdio.h>
#include <sys/types.h>
#include <sys/socket.h>
#include <netinet/in.h>
#include <netdb.h>
#include <stdlib.h>
#include <string.h>
#include <unistd.h>

int main(int argc, char** argv)
{
	struct sockaddr_in servaddr;
	struct hostent *hp;
	int sock_id;
	char message[1024*1024] = {0};
	int msglen;
	char request[] = "GET /index.html HTTP/1.0\n"
	"From: slava!!!\nUser-Agent: wget_sortof by slava\n\n";

	//Get a socket
	if((sock_id = socket(AF_INET, SOCK_STREAM, 0)) == -1) {
		fprintf(stderr,"Couldn't get a socket.\n"); exit(EXIT_FAILURE);
	}
	else {
		fprintf(stderr,"Got a socket.\n");
	}

	//book uses bzero which my man pages say is deprecated
	//the man page said to use memset instead. :-)
	memset(&servaddr,0,sizeof(servaddr));

	//get address for google.com
	if((hp = gethostbyname("google.com")) == NULL) {
		fprintf(stderr,"Couldn't get an address.\n"); exit(EXIT_FAILURE);
	}
	else {
		fprintf(stderr,"Got an address.\n");
	}

	//bcopy is deprecated also, using memcpy instead
	memcpy((char *)&servaddr.sin_addr.s_addr, (char *)hp->h_addr, hp->h_length);

	//fill int port number and type
	servaddr.sin_port = htons(80);
	servaddr.sin_family = AF_INET;

	//make the connection
	if(connect(sock_id, (struct sockaddr *)&servaddr, sizeof(servaddr)) != 0) {
		fprintf(stderr, "Couldn't connect.\n");
	}
	else {
		fprintf(stderr,"Got a connection!!!\n");
	}

	//NOW THE HTTP PART!!!

	//send the request
	write(sock_id,request,strlen(request));

	//read the response
	msglen = read(sock_id,message,1024*1024);

	printf("response is %d bytes long\n", msglen);

	//print the reasponse
	printf("%s", message);

	return 0;
}[/php]

---

