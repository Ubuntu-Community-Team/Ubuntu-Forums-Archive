---
title: "dereferencing pointer to incomplete type"
date: 2012-10-03
forum: Programming Talk
---

### Post by rushikesh988 on 2012-10-03
Hello friends I am trying to compile this C program for client socket programming but getting the error:
> client.c:18:8: warning: assignment from incompatible pointer type [enabled by default]
client.c:25:47: error: dereferencing pointer to incomplete type



> #include<sys/socket.h>
#include<sys/types.h>
#include<netinet/in.h>
#include<netdb.h>
#include<stdio.h>
#include<string.h>
#include<stdlib.h>
#include<unistd.h>
#include<errno.h>

int main()
	{
 		int sock, bytes_received;
		char send_data[1024],recv_data[1024];
		struct hostnet *host;
		struct sockaddr_in server_addr;
		
		host = gethostbyname("192.168.1.1");
		if ((sock = socket(AF_INET ,SOCK_STREAM , 0)) == -1)  {
		     perror("Socket");
		     exit(1);
		}
server_addr.sin_family = AF_INET;
server_addr.sin_port = htons(5000);
server_addr.sin_addr = *((struct in_addr*)host->h_addr);
bzero(&(server_addr.sin_zero),8 );

if(connect(sock, (struct sockaddr *)&server_addr,sizeof(struct sockaddr)) == -1)
{
perror("connect");
exit(1);
}
while(1)
{
bytes_received=recv(sock,recv_data,1024,0);
recv_data[bytes_received] = '\0';

if(strcmp(recv_data , "q") == 0 || strcmp(recv_data , "Q") == 0)
{
close(sock);
break;
}
else
printf("\nreceived data at client side = %s " , recv_data);
printf("\nSEND(q or Q to quit) :");
gets(send_data);
if(strcmp(send_data , "q") !=0 && strcmp(send_data , "Q") !=0)
send(sock,send_data,strlen(send_data), 0);
else
{
send(sock,send_data,strlen(send_data), 0);
close(sock);
break;
}
}
return 0;
}

please help me in solving the error of DEREFERENCING  which is in the following line:> server_addr.sin_addr = *((struct in_addr*)host->h_addr);

---

### Post by Zugzwang on 2012-10-03
You have a typo: It should be "struct hostent" and not "struct hostnet" in line 15. With the latter, you in a sense forward-declare a new structure type "hostnet", but never define it, which is the source of the warning and error messages. With "struct hostent", your code compiles fine (here).

---

### Post by rushikesh988 on 2012-10-03
Thank you so much !!! now code compiles fine...

---

