---
title: "recv() is not receiving everything."
date: 2009-02-01
forum: Programming Talk
---

### Post by mameth on 2009-02-01
Hi everybody!
I wrote some code to get html from web pages. here's the code:
```

#include <sys/types.h>
#include <sys/socket.h>
#include <sys/un.h>
#include <stddef.h>
#include <stdlib.h>
#include <errno.h>
#include <string.h>
#include <stdio.h>
#include <netdb.h>
#include <unistd.h>
int main()
{
	char ch;
	char web_address_temp[60];
	char *web_address=NULL;
	int i=0;
	int dummy=0;
	printf("Write the address you wanted to visit: ");
	scanf("%c",&ch);
	while(ch!='\n')
	{
		web_address_temp[i] = ch;
		scanf("%c",&ch);
		i++;
	}
	web_address = (char *) realloc(NULL,strlen(web_address_temp)*sizeof(char));
	strcpy(web_address,web_address_temp);
	/*
	char *web_host=NULL;
	i=0;
	dummy = strlen(web_address);
	while(web_address[i]!='/')
	{
	    if(i>=dummy)
	    {
	        break;
	    }
		web_address_temp[i] = web_address[i];
		i++;
	}
	web_address_temp[i] = '\0';
	web_host = (char *)realloc(NULL,strlen(web_address_temp)*sizeof(char));
	*/
	int sockid=0;
	int conn=0;
	char msgbuff_temp[100];
	strcpy(msgbuff_temp,"GET / HTTP/1.1\nHost: ");
	strcat(msgbuff_temp, web_address);
	strcat(msgbuff_temp, "\nUser-Agent: Mozilla/4.0 (compatible; MSIE 7.0; Windows NT 5.1)\n\n\0");
	dummy = strlen(msgbuff_temp);
	char *msgbuff=NULL;
	msgbuff = (char *)realloc(NULL,dummy*sizeof(char));
	strcpy(msgbuff,msgbuff_temp);
	struct addrinfo hints, *res;
	memset(&hints,0,sizeof(hints));
	hints.ai_family = AF_UNSPEC;
	hints.ai_socktype = SOCK_STREAM;
	getaddrinfo(web_address,"80",&hints,&res);
	sockid = socket(res->ai_family, res->ai_socktype, res->ai_protocol);
	if(sockid<0)
	{
		perror("socket");
		close(sockid);
		return 0;
	}
	conn = connect(sockid,res->ai_addr,res->ai_addrlen);
	if(conn<0)
	{
		perror("connect");
		close(sockid);
		return 0;
	}
	dummy = send(sockid,msgbuff, strlen(msgbuff),0);
	if(dummy<0)
	{
		perror("send");
		close(sockid);
		return 0;
	}

	char msgbuff_recv[130000];
	memset(&msgbuff_recv,'\0',sizeof(msgbuff_recv));
	int recv_byts;
	recv_byts =recv(sockid,msgbuff_recv,sizeof(msgbuff_recv),0);
	msgbuff_recv[recv_byts] ='\0';
	if(recv_byts<=0)
	{
		perror("recv");
		close(sockid);
		return 0;
	}
	FILE * fid;
	fid = fopen("try.html","w");
	for(i=0; i<= recv_byts; i++)
	{
		printf("%c",msgbuff_recv[i]);
		fprintf(fid,"%c",msgbuff_recv[i]);
	}
	printf("\n");
	close(sockid);
	free(res);
	free(web_address);
	return 0;
}

```

recv function only receives some part of the html code, not all of it. i will use this code to build up some browser, so i need the full html of a page.
by the way, i changed the buffer size alot(i mean i have already written some values like 10000000) so i believe this isn't about the size.

---

### Post by stroyan on 2009-02-01
recv() doesn't wait for every byte that the server sends in reply.  It returns whatever bytes are available so far.  You may need to call it more than once to get all of the reply.  The "man recv" page states that.

I noticed that you used "sizeof(char)".  That is always one, as sizeof is defined to return the size of a type in chars.

I also noticed that you are using strlen() to compute a size to copy a string into.  But a string requires strlen()+1 chars because of the trailing NULL byte that is copied.

Check that you are freeing all the memory that you allocate, particularly in the error return code.

---

### Post by dwhitney67 on 2009-02-01
I assume from your code that you are using a TCP socket.  When a message or messages are sent by a server, the client application cannot assume that the message(s) will arrive in one complete packet.

The client application may have to define a while-loop or other looping structure to receive data from the server until recv() returns zero (indicating zero bytes were read) or an error occurs.  It is up to the client application to collate all of the data received into the buffer that it manages.

Read the man-page for recv() to get a clearer idea of what the function returns.

---

### Post by mameth on 2009-02-02
Thank you for your replies. I will investigate on it. I did a google search for several times about this, but i couldn't find a solution. I have recently stopped using MS and i haven't get used to the idea of having something like man. 
Anyway, thanks again.

---

### Post by Gulyan on 2009-02-02
I think this should work:
```
#include <sys/types.h>
#include <sys/socket.h>
#include <sys/un.h>
#include <stddef.h>
#include <stdlib.h>
#include <errno.h>
#include <string.h>
#include <stdio.h>
#include <netdb.h>
#include <unistd.h>
int main()
{
	char ch;
	char web_address_temp[60];
	char *web_address=NULL;
	int i=0;
	int dummy=0;
	printf("Write the address you wanted to visit: ");
	scanf("%c",&ch);
	while(ch!='\n')
	{
		web_address_temp[i] = ch;
		scanf("%c",&ch);
		i++;
	}
	web_address = (char *) realloc(NULL,strlen(web_address_temp)*sizeof(char));
	strcpy(web_address,web_address_temp);
	/*
	char *web_host=NULL;
	i=0;
	dummy = strlen(web_address);
	while(web_address[i]!='/')
	{
	    if(i>=dummy)
	    {
	        break;
	    }
		web_address_temp[i] = web_address[i];
		i++;
	}
	web_address_temp[i] = '\0';
	web_host = (char *)realloc(NULL,strlen(web_address_temp)*sizeof(char));
	*/
	int sockid=0;
	int conn=0;
	char msgbuff_temp[100];
	strcpy(msgbuff_temp,"GET / HTTP/1.1\nHost: ");
	strcat(msgbuff_temp, web_address);
	strcat(msgbuff_temp, "\nUser-Agent: Mozilla/4.0 (compatible; MSIE 7.0; Windows NT 5.1)\n\n\0");
	dummy = strlen(msgbuff_temp);
	char *msgbuff=NULL;
	msgbuff = (char *)realloc(NULL,dummy*sizeof(char));
	strcpy(msgbuff,msgbuff_temp);
	struct addrinfo hints, *res;
	memset(&hints,0,sizeof(hints));
	hints.ai_family = AF_UNSPEC;
	hints.ai_socktype = SOCK_STREAM;
	getaddrinfo(web_address,"80",&hints,&res);
	sockid = socket(res->ai_family, res->ai_socktype, res->ai_protocol);
	if(sockid<0)
	{
		perror("socket");
		close(sockid);
		return 0;
	}
	conn = connect(sockid,res->ai_addr,res->ai_addrlen);
	if(conn<0)
	{
		perror("connect");
		close(sockid);
		return 0;
	}
	dummy = send(sockid,msgbuff, strlen(msgbuff),0);
	if(dummy<0)
	{
		perror("send");
		close(sockid);
		return 0;
	}

	char msgbuff_recv[130000];
	memset(&msgbuff_recv,'\0',sizeof(msgbuff_recv));
	int recv_byts;

	recv_byts =recv(sockid,msgbuff_recv,sizeof(msgbuff_recv),0);
	msgbuff_recv[recv_byts] ='\0';
	if(recv_byts<=0)
	{
		perror("recv");
		close(sockid);
		return 0;
	}
	FILE * fid;
	fid = fopen("try.html","w");
	[COLOR="Red"]do{[/COLOR]
	for(i=0; i<= recv_byts; i++)
	{
		printf("%c",msgbuff_recv[i]);
		fprintf(fid,"%c",msgbuff_recv[i]);
	}
[COLOR="Red"]	recv_byts =recv(sockid,msgbuff_recv,sizeof(msgbuff_recv),0);
	}while(recv_byts >= 0);[/COLOR]
	printf("\n");
	close(sockid);
	free(res);
	free(web_address);
	return 0;
}
```

Note that it is not the most effective way of getting the html code

---

### Post by dwhitney67 on 2009-02-02
I do not know if this is more efficient or not, but in C++ I would do something like:
[php]
...
TCPServerSocket sock;
sock.Connect(web_address, 80);

sock.Send(request.c_str(), request.size());

size_t bytesRcvd = 0;

do
{
  char buf[1024] = {0};
  bytesRcvd = sock.Recv(buf, sizeof(buf));
  std::cout << buf;
} while (bytesRcvd > 0);
...
[/php]
The output written to standard-out can be redirected to a file if needed.

---

### Post by mameth on 2009-02-03
Thanks again for your replies. Finally i can receive the whole html. But when i make a html page file from the received buffer, i can see that the code is duplicated several times. how can i prevent that?

---

### Post by mameth on 2009-02-05
I have also solved the problem using MSG_WAITALL flag.

---

