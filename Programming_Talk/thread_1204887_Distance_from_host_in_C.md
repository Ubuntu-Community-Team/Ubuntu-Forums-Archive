---
title: "Distance from host in C"
date: 2009-07-05
forum: Programming Talk
---

### Post by C4nc3l on 2009-07-05
Hi all, 
I'm searching for a way to calculate distance between two host in my C program.
I have an already open TCP socket, so i would like to use the ttl in ip header from that connection, but when i try to get it with this code (where line is the message from the client): 
```

ip_reply=malloc(sizeof(struct iphdr));
ip_reply = (struct iphdr*) line;
printf("ID: %d\n", ntohs(ip_reply->id));
printf("TTL: %d\n", ip_reply->ttl);
printf("tot_len: %d\n", ip_reply->tot_len);
printf("frag_off:%d\n", ip_reply->frag_off);
printf("protocol: %d\n", ip_reply->protocol);
```

It works, but ttl and others fields doesn't match with any real IP header i see in wireshark capture, what's wrong?

There exist other way to calculate distance between two host others than TTL and a sort of round trip time i've already implemented?

PS: I know there's no way to get a good approximation of distance nor with TTL nor with time... but for my intention it's ok...

Bye

---

### Post by dwhitney67 on 2009-07-05
I presume you have created a raw socket, one for the sender, the other for the receiver?

Something like:
```

int sd = socket(AF_INET, SOCK_RAW, IPPROTO_TCP);

```

When the server receives the data, using something like:
```

char buf[1024];

...

int client_sd = accept(sd, 0, 0);

...

int bytesRcvd = recv(client_sd, buf, sizeof(buf), 0);

```

The IP header data can be obtained using something similar to the following:
```

const struct ip* iph = (const struct ip*) buf;

...

printf("ID       : %d\n", ntohs(iph->ip_id));
printf("TTL      : %d\n", iph->ip_ttl);
printf("total len: %d\n", ntohs(iph->ip_len));
printf("off      : %d\n", iph->ip_off);
printf("protocol : %d\n", iph->ip_p);

```

---

### Post by C4nc3l on 2009-07-05
> **dwhitney67 said:**
> I presume you have created a raw socket, one for the sender, the other for the receiver?

Something like:
```

int sd = socket(AF_INET, SOCK_RAW, IPPROTO_TCP);

```

When the server receives the data, using something like:
```

char buf[1024];

int bytesRcvd = recv(sd, buf, sizeof(buf), 0);

```

The IP header data can be obtained using something similar to the following:
```

const struct ip* iph = (const struct ip*) buf;

...

printf("ID       : %d\n", ntohs(iph->ip_id));
printf("TTL      : %d\n", iph->ip_ttl);
printf("total len: %d\n", ntohs(iph->ip_len));
printf("off      : %d\n", iph->ip_off);
printf("protocol : %d\n", iph->ip_p);

```

Thanks for the response.

Ehm no, i've created a SOCK_STREAM with:
```
socket(AF_INET, SOCK_STREAM, 0)
```
I don't want to use RAW socket because they ask for root permissions... this can be a problem? Why i don't see any error about this?

I've tried to use your code...  gcc return:
```
error: dereferencing pointer to incomplete type
``` 
for every time i try to access to things in the struct.
It's something like i don't have a struct ip, the only one that exists is iphdr...

---

### Post by dwhitney67 on 2009-07-05
> **C4nc3l said:**
> Thanks for the response.

Ehm no, i've created a SOCK_STREAM with:
```
socket(AF_INET, SOCK_STREAM, 0)
```
I don't want to use RAW socket because they ask for root permissions... this can be a problem? Why i don't see any error about this?

You're welcome.  If you want to examine IP/TCP header information, it is my understanding that you will need to create a raw socket... at least on the receiver (server?) end.

If you merely create a SOCK_STREAM, then you will only receive the message datagram, not the header information.

> **C4nc3l said:**
> 
I've tried to use your code...  gcc return:
```
error: dereferencing pointer to incomplete type
``` 
for every time i try to access to things in the struct.
It's something like i don't have a struct ip, the only one that exists is iphdr...
You will need to include the following header files:
```

#include <netinet/ip.h>    /* for IP header */
#include <netinet/tcp.h>   /* if you want to examine TCP header */

```
My knowledge of raw sockets is not the best; when I compiled my test application, I noticed that _USE_BSD was defined (automagically) and that "struct ip" was available.  My test code was compiled on a Linux system.

If you need help working with sockets, you can look at my [socket library]("http://softhouseproductions.com/SocketLibrary.tgz").  Within the examples I provide, I have one (in C++) that employs raw sockets, but for UDP.  It wouldn't take much to get it to work with TCP.

---

### Post by C4nc3l on 2009-07-05
> **dwhitney67 said:**
> You're welcome.  If you want to examine IP/TCP header information, it is my understanding that you will need to create a raw socket... at least on the receiver (server?) end.

If you merely create a SOCK_STREAM, then you will only receive the message datagram, not the header information.



Ok thanks, it's a bad news for me... but now i know :)
I thought that also with stream i can access to ip header... so the results are sadly casual number :(
One of my objectives it's to avoid root permission so i can't use raw socket, you know another ways to get a host distance?
> **dwhitney67 said:**
> 
You will need to include the following header files:
```

#include <netinet/ip.h>    /* for IP header */
#include <netinet/tcp.h>   /* if you want to examine TCP header */

```

ok, i include  "linux/ip.h" naturally i see other structs...
> **dwhitney67 said:**
> 
My knowledge of raw sockets is not the best; when I compiled my test application, I noticed that _USE_BSD was defined (automagically) and that "struct ip" was available.  My test code was compiled on a Linux system.

If you need help working with sockets, you can look at my [socket library]("http://softhouseproductions.com/SocketLibrary.tgz").  Within the examples I provide, I have one (in C++) that employs raw sockets, but for UDP.  It wouldn't take much to get it to work with TCP.
Thanks a lot for the help, you clarify some situation that was obscure to me, however you drastically remove my hopes of use tcp socket to see the ttl :p

---

