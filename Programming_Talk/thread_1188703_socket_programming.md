---
title: "socket programming"
date: 2009-06-16
forum: Programming Talk
---

### Post by polarbear12345 on 2009-06-16
i m getting **invalid argument error in accept** in the following code:
this is actually rough chat server.(server will accept a msg from a client and send to all connected clients)....
```
#include<sys/socket.h>
#include<sys/types.h>
#include<string.h>
#include<netinet/in.h>
#include<sys/select.h>
#include<unistd.h>
#include<stdlib.h>
#include<stdio.h>
int main()
{
	int listenfd=socket(AF_INET,SOCK_STREAM,0);
	if(listenfd==-1)
	{
		printf("socket error in server\n");
		exit(0);
	}
	struct sockaddr_in saddr;
	bzero(&saddr,sizeof(saddr));
	saddr.sin_family=AF_INET;
	saddr.sin_port=htons(9000);
	saddr.sin_addr.s_addr=htonl(INADDR_ANY);
	int res=bind(listenfd,(struct sockaddr*)&saddr,sizeof(saddr));
	if(res==-1)
	{
		printf("bind error in server\n");
		exit(0);
	}
	res=listen(listenfd,10);
	if(res==-1)
	{
		printf("listen error in server\n");
		exit(0);
	}
	fd_set fd_rd;
	int clifd[100]={-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1};
	int cliconn=0;	
	for(;;)
	{
		FD_ZERO(&fd_rd);
		FD_SET(listenfd,&fd_rd);
		int j=0,i;
		int maxfd=listenfd;
		for(i=0;i<100;i++)
		{
			if(j==cliconn)
				break;
			else if(clifd[i]!=-1)
			{
				FD_SET(clifd[i],&fd_rd);
				j++;
				if(clifd[i]>maxfd)
					maxfd=clifd[i];
			}
		}
		int activefd=select(maxfd+1,&fd_rd,NULL,NULL,NULL);
		//printf("fromfromfrom\n");		
		if(activefd==-1)
		{
			printf("select error in server\n");
			exit(0);
		}
		else if(FD_ISSET(listenfd,&fd_rd))
		{
			
			struct sockaddr_in cliaddr;
			bzero(&cliaddr,sizeof(cliaddr));
			socklen_t clilen;
			int i;
			int connfd=accept(listenfd,(struct sockaddr*)&cliaddr,&clilen);
			if(connfd==-1)
			{
				printf("accept error in server\n");
				perror("accept");
				//exit(0);
			}
			cliconn++;
			for(i=0;i<cliconn;i++)
			{
				if(clifd[i]==-1)
				{
					clifd[i]=connfd;
					break;
				}
			}
			printf("new client connected\n");//exit(0);
		}
		else
		{
			int i;
			for(i=0;i<cliconn;i++)
			{
				if(FD_ISSET(clifd[i],&fd_rd))
				{
					char buff[200];
					int n=read(clifd[i],buff,sizeof(buff));
					if(n==0)
					{
						close(clifd[i]);
						clifd[i]=-1;
						cliconn--;
					}
					else if(n==-1)
					{
						printf("client terminated unusually\n");
						continue;
					}
					else if(n>0)
					{
						buff[n]='\n';
						int j;
						for(j=0;j<cliconn;j++)
						{
							if(clifd[j]!=-1)
							{
								write(clifd[j],buff,n+1);
								printf("ddwdwdwdwdwd");
							}
						}					
					}
				}
			}
		}
	}
	return 0;
}
```

---

### Post by jordanmthomas on 2009-06-16
This may be better answered in the programming section of ubuntuforums, and you may want to use the code tags around your code next time.

For what it's worth, the code you posted compiles and seems to run with no issue here, though I did not have a client with which to connect to it.

---

### Post by PmDematagoda on 2009-06-16
Moved to Programming Talk.

To the OP, please repost the code using the code tags or php tags(whatever you prefer) and please use proper indentation and spacing, it is not very pleasant to read through the code you just posted.

---

### Post by polarbear12345 on 2009-06-16
The 3rd argument to accept cannot be negetive

so 1st initialize clilen=0 during declaration and then use it as
accept argument...

---

### Post by PmDematagoda on 2009-06-16
```
#include<sys/socket.h>
#include<sys/types.h>
#include<string.h>
#include<netinet/in.h>
#include<sys/select.h>
#include<unistd.h>
#include<stdlib.h>
#include<stdio.h>
int main()
{
	int listenfd=socket(AF_INET,SOCK_STREAM,0);
	if(listenfd==-1)
	{
		printf("socket error in server\n");
		exit(0);
	}
	struct sockaddr_in saddr;
	bzero(&saddr,sizeof(saddr));
	saddr.sin_family=AF_INET;
	saddr.sin_port=htons(9000);
	saddr.sin_addr.s_addr=htonl(INADDR_ANY);
	int res=bind(listenfd,(struct sockaddr*)&saddr,sizeof(saddr));
	if(res==-1)
	{
		printf("bind error in server\n");
		exit(0);
	}
	res=listen(listenfd,10);
	if(res==-1)
	{
		printf("listen error in server\n");
		exit(0);
	}
	fd_set fd_rd;
	int clifd[100]={-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1};
[COLOR="Red"]	int cliconn=0;	[/COLOR]
	for(;;)
	{
		FD_ZERO(&fd_rd);
		FD_SET(listenfd,&fd_rd);
		[COLOR="Red"]int j=0[/COLOR],i;
		int maxfd=listenfd;
		for(i=0;i<100;i++)
		{
[COLOR="Red"]			if(j==cliconn)[/COLOR]
				break;
			else if(clifd[i]!=-1)
			{
				FD_SET(clifd[i],&fd_rd);
				j++;
				if(clifd[i]>maxfd)
					maxfd=clifd[i];
			}
		}
		int activefd=select(maxfd+1,&fd_rd,NULL,NULL,NULL);
		//printf("fromfromfrom\n");		
		if(activefd==-1)
		{
			printf("select error in server\n");
			exit(0);
		}
		else if(FD_ISSET(listenfd,&fd_rd))
		{
			
[COLOR="Red"]**			struct sockaddr_in cliaddr;**[/COLOR]
			bzero(&cliaddr,sizeof(cliaddr));
[COLOR="Red"]**			socklen_t clilen;**[/COLOR]
			int i;
			int connfd=accept(listenfd,(struct sockaddr*)&cliaddr,&clilen);
			if(connfd==-1)
			{
				printf("accept error in server\n");
				perror("accept");
				//exit(0);
			}
			cliconn++;
			for(i=0;i<cliconn;i++)
			{
				if(clifd[i]==-1)
				{
					clifd[i]=connfd;
					break;
				}
			}
			printf("new client connected\n");//exit(0);
		}
		else
		{
			int i;
			for(i=0;i<cliconn;i++)
			{
				if(FD_ISSET(clifd[i],&fd_rd))
				{
					char buff[200];
					int n=read(clifd[i],buff,sizeof(buff));
					if(n==0)
					{
						close(clifd[i]);
						clifd[i]=-1;
						cliconn--;
					}
					else if(n==-1)
					{
						printf("client terminated unusually\n");
						continue;
					}
					else if(n>0)
					{
						buff[n]='\n';
						int j;
						for(j=0;j<cliconn;j++)
						{
							if(clifd[j]!=-1)
							{
								write(clifd[j],buff,n+1);
								printf("ddwdwdwdwdwd");
							}
						}					
					}
				}
			}
		}
	}
	return 0;
}
```
The coloured lines seem to be in conflict with each other, you set both j and cliconn to zero, then check the two to see if they equal **before** you've done anything on them and then break out of the loop, so nothing has changed for both the variables and from the way you structured the code, never will, why do you have that condition in the first place anyway?

Also some advice for the style of writing code, you seem to be using the rule in C99 which allows for scattering of variable declarations within the code, while it is allowed, I do not really agree with it and if you look at places like the Linux kernel and many other projects, they don't like that either, so my advice is to declare all the variables you are going to use at the start of the function itself so it can be easy to reference the variables and the code doesn't get messed up.

Also, regarding your use of bzero(), the bzero() man has this to say:-
> CONFORMING TO
       4.3BSD.   This  function   is   deprecated   (marked   as   LEGACY   in
       POSIX.1-2001): use memset(3) in new programs.  POSIX.1-2008 removes the
       specification of bzero().

Edit:- Additionally, you are using accept when clilen has not been initialised, the accept() man states:-
>        int accept(int sockfd, struct sockaddr *addr, socklen_t *addrlen);

       The argument addr is a pointer to a sockaddr structure.  This structure
       is filled in with the address of the peer socket, as known to the  com-
       munications  layer.   The  exact format of the address returned addr is
       determined by the  socket&#8217;s  address  family  (see  socket(2)  and  the
       respective  protocol  man pages).  When addr is NULL, nothing is filled
       in; in this case, addrlen is not used, and should also be NULL.

[B][U]       The addrlen argument is a value-result argument: the caller  must  ini-
       tialize  it  to contain the size (in bytes) of the structure pointed to
       by addr; on return it will contain the actual size of the peer address.[/U][/B]

       The  returned address is truncated if the buffer provided is too small;
       in this case, addrlen will return a value greater than was supplied  to
       the call.
so that maybe your error, using an uninitialised variable.

Edit 2:-
Please, don't take this badly, but you shouldn't keep declaring variables of similar names over and over again, you should also use more meaningful variable names than a generic "i" or "j", as your program gets larger, this will become a problem, so you should solve it at the beginning.

---

