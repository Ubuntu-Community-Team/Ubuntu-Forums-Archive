---
title: "socket problem"
date: 2012-06-13
forum: Programming Talk
---

### Post by chuchi on 2012-06-13
Hi all!!
 

 I am developing a TCP network application using sockets. The client sends continuously strings using “send”. The server receives these strings with “recv” and prints them onto the screen.
 

 Server code
 

 ```

 		//socket()
 		//bind …
 		//accept
 		for(;;)
 		{
 			if((recv(connfd, buff, TAM_BUFF,0)) ==-1)
 			{
 				perror("error receving data\n");
 			}
 			else
 				printf("Data received=%s\n",buff);
 		}
 
```
 

 And the client code
 

 ```

 	//socket
 	//connect
 	printf("input something to send to the server\n");
 	for(;;)
 	{
 		scanf("%s",recvline);
 		n=send(sockfd,recvline,TAM_BUFF,0);//here send return TAM_BUFF, even with the other pair is down
 		if(n ==-1) //this is never executed
 		{
 			perror("send client error");
 		}
 		else printf("%d bytes written to the server\n",n);
 	}	
 
```
 

 So I kill the server with “kill -9 pid”. The first time I input something in the client after killing the server, the “send” call still returns TAM_BUFF, and the second time the client program just exits....  
 

 Why?? What happens??  
 

 Thank you very very much!!

---

