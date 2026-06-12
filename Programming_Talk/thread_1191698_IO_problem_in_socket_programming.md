---
title: "I/O problem in socket programming"
date: 2009-06-19
forum: Programming Talk
---

### Post by polarbear12345 on 2009-06-19
**the program below is to print the IP address of the connected client on server side**
however,cout and other C++ stream objects are not working..
however function:
ssize_t write(int fd, const void *buf, size_t count)
is working.....
plzz give me reasons for this odd behaviour and also a possible solution to write in a file the obtained IP address in the for(;;) loop below using C++ stream objects

```
#include<sys/socket.h>
#include<errno.h>
#include<sys/types.h>
#include<arpa/inet.h>
#include<stdlib.h>
#include<unistd.h>
#include<stdio.h>
#include<string.h>
#include<fstream>
#include<iostream>
#define TIME_TO_REFRESH_LOG 60
using namespace std;
int main()
{
	int listenfd=socket(AF_INET,SOCK_STREAM,0);
	if(listenfd==-1)
	{
		perror("server socket");
		exit(1);
	}
	struct sockaddr_in servaddr;
	bzero(&servaddr,sizeof(servaddr));
	servaddr.sin_family=AF_INET;
	servaddr.sin_port=htons(9001);
	servaddr.sin_addr.s_addr=htonl(INADDR_ANY);
	if(bind(listenfd,(struct sockaddr*)&servaddr,sizeof(servaddr))==-1)
	{
		perror("server bind");
		exit(1);
	}
	if(listen(listenfd,128)==-1)
	{
		perror("server listen");
		exit(1);
	}
	int connfd;
	struct sockaddr_in cliaddr;
	socklen_t clilen;
	for(;;)
	{
		bzero(&cliaddr,sizeof(cliaddr));
		clilen=sizeof(cliaddr);
		connfd=accept(listenfd,(struct sockaddr*)&cliaddr,&clilen);		
		if(connfd==-1)
		{
			perror("server accept");	
			//continue;
		}
		char buf[100];
		inet_ntop(AF_INET,&cliaddr.sin_addr,buf,sizeof(buf));
		cout<<buf;//not working
		write(1,buf,100);//working
		close(connfd);
	}	
	return 0;
}

```

---

### Post by polarbear12345 on 2009-06-19
the program below is to print the IP address of the connected client on server side
however,cout and other C++ stream objects are not working..
however function:
ssize_t write(int fd, const void *buf, size_t count)
is working.....
plzz give me reasons for this odd behaviour and also a possible solution to write in a file the obtained IP address in the for(;;) loop below using C++ stream objects

```
#include<sys/socket.h>
#include<errno.h>
#include<sys/types.h>
#include<arpa/inet.h>
#include<stdlib.h>
#include<unistd.h>
#include<stdio.h>
#include<string.h>
#include<fstream>
#include<iostream>
#define TIME_TO_REFRESH_LOG 60
using namespace std;
int main()
{
	int listenfd=socket(AF_INET,SOCK_STREAM,0);
	if(listenfd==-1)
	{
		perror("server socket");
		exit(1);
	}
	struct sockaddr_in servaddr;
	bzero(&servaddr,sizeof(servaddr));
	servaddr.sin_family=AF_INET;
	servaddr.sin_port=htons(9001);
	servaddr.sin_addr.s_addr=htonl(INADDR_ANY);
	if(bind(listenfd,(struct sockaddr*)&servaddr,sizeof(servaddr))==-1)
	{
		perror("server bind");
		exit(1);
	}
	if(listen(listenfd,128)==-1)
	{
		perror("server listen");
		exit(1);
	}
	int connfd;
	struct sockaddr_in cliaddr;
	socklen_t clilen;
	for(;;)
	{
		bzero(&cliaddr,sizeof(cliaddr));
		clilen=sizeof(cliaddr);//changed after below      //discussion from clilen=0 
		connfd=accept(listenfd,(struct sockaddr*)&cliaddr,&clilen);		
		if(connfd==-1)
		{
			perror("server accept");	
			//continue;
		}
		char buf[100];
		inet_ntop(AF_INET,&cliaddr.sin_addr,buf,sizeof(buf));
		cout<<buf;//not working in loop
		write(1,buf,100);//working
		close(connfd);
	}	
	return 0;
}
```

---

### Post by dwhitney67 on 2009-06-19
An excerpt from the man-page for accept()...

```

...
 The addrlen argument is a value-result argument: it should initially contain the size
of the  structure pointed to by addr; on return it will contain the actual length
(in bytes) of the address returned. When addr is NULL nothing is filled in.

```
In your code, you set this value to a zero.

You then want to try something like:
```

const char*          sourceAddr = inet_ntoa(addr.sin_addr);
const unsigned short sourcePort = ntohs(addr.sin_port);

```

P.S.  Before you state it, I know... inet_ntoa() is considered deprecated.

---

### Post by dwhitney67 on 2009-06-19
Btw, I tested a TCP server application using the inet_ntop(); the results are either wrong or totally misleading, or I just plain don't understand how to use that function.

Here's a snip of the code I tested with:
```

...
  sockaddr_in addr;
  socklen_t   addrlen = sizeof(addr);

  int clntSock = accept(sd, (sockaddr*) &addr, &addrlen);

  std::cout << "client connected... ";
  char buf[1000] = {0};

  inet_ntop(AF_INET, &addr, buf, sizeof(buf));

  std::cout << buf << std::endl;

  const char*          clntaddr = inet_ntoa(addr.sin_addr);
  const unsigned short clntport = ntohs(addr.sin_port);

  std::cout << "addr = " << clntaddr << ", port = " << clntport << std::endl;

  close(clntSock);

```

The output I got was:
```

client connected... 2.0.169.203
addr = 127.0.0.1, port = 43467

```

---

### Post by smartbei on 2009-06-19
Maybe you need to give inet_ntop addr.sin_addr instead of addr?

```

inet_ntop(AF_INET, addr.sin_addr, buf, sizeof(buf));

```

---

### Post by dwhitney67 on 2009-06-19
> **smartbei said:**
> Maybe you need to give inet_ntop addr.sin_addr instead of addr?

Yes, thank you, that is correct.  I should have paid more attention to the OP's code.

---

### Post by polarbear12345 on 2009-06-19
well guys my problem is that when i use cout in above for(;;) loop no result is displayed each time a client connects....
Only when i use write() func result is displayed each time a client is connected...

above problem persists only when cout is used in a loop like above

plzzz help

---

### Post by smartbei on 2009-06-19
Maybe it is a buffering problem?

Try cout.flush()...

---

### Post by dwhitney67 on 2009-06-19
> **polarbear12345 said:**
> well guys my problem is that when i use cout in above for(;;) loop no result is displayed each time a client connects....
Only when i use write() func result is displayed each time a client is connected...

above problem persists only when cout is used in a loop like above

plzzz help

Hopefully you heeded my advice from an earlier post.  If not, please fix the following:
```

	struct sockaddr_in cliaddr;
	socklen_t clilen = sizeof(cliaddr);   // <--- Here's the change

```

Btw, this code works:
```

  for (;;)
  {
    int clntSock = accept(sd, (sockaddr*) &cliaddr, &clilen);

    char                 buf[16]  = {0};
    const char*          clntaddr = inet_ntop(AF_INET, &cliaddr.sin_addr, buf, sizeof(buf));
    const unsigned short clntport = ntohs(cliaddr.sin_port);

    std::cout << "addr = " << clntaddr << ", port = " << clntport << std::endl;

    close(clntSock);
  }

```

---

### Post by polarbear12345 on 2009-06-19
i got it due to some reason cout buffer was not being flushed at required time
i used flush(cout)

---

### Post by slavik on 2009-06-19
threads merged.

---

