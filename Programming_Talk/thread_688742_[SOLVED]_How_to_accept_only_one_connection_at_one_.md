---
title: "[SOLVED] How to accept only one connection at one time with socket?"
date: 2008-02-05
forum: Programming Talk
---

### Post by fyplinux on 2008-02-05
Hi, I want to create a socket that only accept one connection at one time, no pending in the list. the new coming connection will be rejected immediately.(**question one**)

On the other hand, if a server socket is connected by other clients, a client should return immediately. (**question two**)

**For question one**, even if I set an limitation by using listen 's** backlog**, arbitrary clients should still connected to the server socket and be pended. I don't know why, in theory, at least, the server socket would only accept as many clients as I set in listen, but It do receive more than the set value

my server socket
```

#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <sys/types.h>
#include <sys/socket.h>
#include <unistd.h>
#include <sys/stat.h>
#include <fcntl.h>
#include <arpa/inet.h>
#include <stdlib.h>

void bind_port(int *local_sock,struct in_addr *addr,int port,int protocol);

int main(int argc, char **argv)
{
	int boot_serv;	
	struct in_addr *addr = malloc(sizeof(struct in_addr));
	if(addr == 0){
		perror("malloc");
		return 0;
	}
	addr->s_addr = htonl (INADDR_ANY);
	
	bind_port(&boot_serv,addr,7778,0);//the local socketT_HXG
	
	if(listen(boot_serv,1) == -1){
		perror("listen\n");
		return 0;
	}
	
	int boot_c;
	socklen_t size = sizeof(struct sockaddr_in);
	struct sockaddr_in *client_saddr = malloc(size); 
	if(client_saddr == 0){
		perror("malloc client addr");
		return 0;
	}
	
	while((boot_c = accept(boot_serv,(struct sockaddr *)client_saddr,&size)) > 0){
		while(1){
			sleep(1);
			if (write(boot_c,"fdf",3) == -1)
				break;
		}
	}

	return 1;
}

//bind the the address and port to a socket 
//protocol , 1, tcp, 0, udp
void bind_port(int *local_sock,struct in_addr *addr,int port,int protocol){
	
	struct sockaddr_in bsaddr;
	bsaddr.sin_family = AF_INET;
	bsaddr.sin_addr.s_addr =  addr->s_addr;////*addr;//or
	//sockaddr.sin_addr.s_addr =  htonl(INADDR_ANY);	
	bsaddr.sin_port = htons(port);
	if(protocol == 0)
		*local_sock = socket(PF_INET,SOCK_STREAM,0);
	else
		*local_sock = socket(PF_INET,SOCK_DGRAM,0);
	
	if(*local_sock == -1){
		perror("bind");
		exit(-1);
	}
	
	if((bind(*local_sock,(struct sockaddr *)&bsaddr,sizeof(bsaddr))) == -1){
		perror("bind ");
		exit(-1);
	}
	
	
}


```

my client socket
```

#include <stdio.h>
#include <stdlib.h>
#include <unistd.h>
#include <errno.h>
#include <string.h>
#include <netdb.h>
#include <sys/types.h>
#include <netinet/in.h>
#include <sys/socket.h>
#include <sys/socket.h>
#include <netinet/in.h>
#include <arpa/inet.h>
#include <fcntl.h>

int main(int argc, char **argv)
{
	
	struct sockaddr_in bsaddr;
	bsaddr.sin_family = AF_INET;
	bsaddr.sin_port = htons(7778);
	//bsaddr.sin_addr =  addr;
	inet_aton("192.168.1.5",(struct in_addr *) &(bsaddr.sin_addr));
	
	
	int local_sock = socket(PF_INET,SOCK_STREAM,0);
	
	if(connect(local_sock,(struct sockaddr *)&bsaddr,sizeof(bsaddr)) == -1){
		perror("connect");
		return 0;
	}
	int packlen = 3;
	char *buf = calloc(packlen+1,sizeof(char));
	if(buf == 0){
		perror("buf");
		return 0;
	}
	
	int n;
	while((n = read(local_sock,buf,packlen)) != -1){
		printf("%s\n",buf);
		memset(buf,0,packlen);
	}
	free(buf);
	
	return 1;
	
}

```

**For question two**, I intended to do it in a way of non-blocking and timeout, Although I found some discussions and code at
[http://www.developerweb.net/forum/archive/index.php/t-3000.html](http://www.developerweb.net/forum/archive/index.php/t-3000.html)
and 
[http://www.developerweb.net/forum/showthread.php?p=13486](http://www.developerweb.net/forum/showthread.php?p=13486)

I still cannot figure out it. 

Any comments would be appreciate.

---

### Post by fyplinux on 2008-02-07
Listen
Created Thursday 07/02/2008

In theory, the socket would queue up to backlog connections, but it does not act in such a way. I tried many times
to get the result that the socket could queue up to arbitrary coming connections.

two ways to solve this problem.

• at the server side, when a new connection is accepted, close the socket, when the accepted connection quit, recreate the socket and listen again.

• at the client side, using select, when there is data coming from the server, it implies the connection is established. when no data coming in a certain period, it implies the server is busy now.

---

