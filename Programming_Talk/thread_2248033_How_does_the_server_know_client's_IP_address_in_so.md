---
title: "How does the server know client's IP address in socket programming?"
date: 2014-10-11
forum: Programming Talk
---

### Post by IAMTubby on 2014-10-11
In socket programming,(TCP as well as UDP), how does the server get to know the client's IP address?
The client only creates a socket(). It does not bind() to an ip address + port number combination, like the server.

How then(in spite of not knowing the ip address) is the server able to send back messages to the client?

I understand that in TCP, the server does
```
newfd = accept(sockfd, (struct sockaddr *)&**cliaddr**, &**cliaddr**_size);
```

And in udp, the server does
```
n = recvfrom(sockfd,mesg,1000,0,(struct sockaddr *)&**cliaddr**,&len);
```

Upon doing these steps, is the client ip address stored in a member of **cliaddr**? Does that mean getting the client IP address is done internally by the accept() and recvfrom() calls?

Thanks.

---

### Post by ofnuts on 2014-10-12
I never used these calls, but when you pass a pointer to something in C calls, in particular when examples use the "&" address-of operator to create the pointer, it's usually because you expect the called function to set values there (their man pages confirm this).

---

