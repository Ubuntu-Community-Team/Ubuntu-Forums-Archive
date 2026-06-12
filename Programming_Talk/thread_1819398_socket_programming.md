---
title: "socket programming"
date: 2011-08-06
forum: Programming Talk
---

### Post by manish411 on 2011-08-06
I am learning socket programming.
Now the prototype of bind()
is int bind(it sockfd, struct sockaddr *my_addr,socklen_t addrlen)
the 2nd parameter is a pointer to the structure sockaddr
but while calling the function the book shows
```

int simpleSocket,returnstatus;
struct sockaddr simpleServer;
returnStatus = bind(simpleSocket,(struct sockaddr *)&simpleServer,sizeof(simpleServer));

```

why cant simply we pass
```

returnstatus = bind(simpleSocket,&simpleServer,sizeof(simpleServer);


```

---

### Post by dwhitney67 on 2011-08-06
I'm surprised to see this:
```

struct sockaddr simpleServer;

```
Typically it would be one of the following:
```

struct sockaddr_in simpleServer;   // IPv4 Socket

struct sockaddr_in6 simpleServer;  // IPv6 Socket

struct sockaddr_un simpleServer;   // Unix/Linux Socket

```
Hence the reason for casting to a pointer to a sockaddr struct.

---

### Post by manish411 on 2011-08-08
yes that was a typing mistake.
So what is the difference between 
```

 struct sockaddr simpleserver;

```
and 
```

struct sockaddr_in simpleserver;

```

---

### Post by psusi on 2011-08-08
sockaddr_in is for an IP4 address.  bind() accepts multiple address families.  Using sockaddr as the argument where the first member identifies what the real structure is is how C does polymorphism.  In C++ terms, you can think of sockaddr_in is a subclass of sockaddr.

---

### Post by karlson on 2011-08-08
> **manish411 said:**
> yes that was a typing mistake.
So what is the difference between 
```

 struct sockaddr simpleserver;

```
and 
```

struct sockaddr_in simpleserver;

```

The first is generic socket address structure, the second one is the structure specific to Internet addressing, in this case IPv4 addressing.

---

### Post by manish411 on 2011-08-10
Thanks!!! That surely cleared my doubts!!!

---

### Post by worseisworser on 2011-08-10
While on the topic of socket programming, and in case you don't know; this is a pretty good and quick guide to this stuff:
  [http://beej.us/guide/bgnet/output/html/multipage/index.html](http://beej.us/guide/bgnet/output/html/multipage/index.html)

---

