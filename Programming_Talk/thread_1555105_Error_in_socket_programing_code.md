---
title: "Error in socket programing code"
date: 2010-08-17
forum: Programming Talk
---

### Post by piyush.neo on 2010-08-17
i copied this code (for showing ip for host name) from famous beej guide for socket programming .
It was working fine on ubuntu 9.10 but giving an error on Ubuntu 10.04..
```
piyush@piyush-laptop:~/codes/netwrkcod$ cc sample.c 
piyush@piyush-laptop:~/codes/netwrkcod$ ./a.out www.google.com
getaddrinfo: No address associated with hostname

```
```

#include   <stdio.h>
#include   <string.h>
#include   <sys/types.h>
#include   <sys/socket.h>
#include   <netdb.h>
#include   <arpa/inet.h>
int main(int argc, char *argv[])
{
       struct addrinfo hints, *res, *p;
       int status;
       char ipstr[INET6_ADDRSTRLEN];
       if (argc != 2) {
           fprintf(stderr,"usage: showip hostname\n");
           return 1;
       }
       memset(&hints, 0, sizeof hints);
       hints.ai_family = AF_INET; // AF_INET or AF_INET6 to force version
       hints.ai_socktype = SOCK_STREAM;
       if ((status = getaddrinfo(argv[1], NULL, &hints, &res)) != 0) {
           fprintf(stderr, "getaddrinfo: %s\n", gai_strerror(status));
           return 2;
       }
       printf("IP addresses for %s:\n\n", argv[1]);
       for(p = res;p != NULL; p = p->ai_next) {
           void *addr;
           char *ipver;
           // get the pointer to the address itself,
           // different fields in IPv4 and IPv6:
           if (p->ai_family == AF_INET) { // IPv4
                 struct sockaddr_in *ipv4 = (struct sockaddr_in *)p->ai_addr;
                 addr = &(ipv4->sin_addr);
                 ipver = "IPv4";
           } else { // IPv6
                 struct sockaddr_in6 *ipv6 = (struct sockaddr_in6 *)p->ai_addr;
                 addr = &(ipv6->sin6_addr);
                 ipver = "IPv6";
           }
           // convert the IP to a string and print it:
           inet_ntop(p->ai_family, addr, ipstr, sizeof ipstr);
           printf(" %s: %s\n", ipver, ipstr);
       }
       freeaddrinfo(res); // free the linked list
       return 0;
 }


```
Plz help...Ubuntu 10.04 seems to have a lot of bugs....:confused:

---

### Post by gmargo on 2010-08-18
It works fine for me on both 10.04 Lucid and 8.04 Hardy.  (IPv4)

---

### Post by piyush.neo on 2010-08-18
well i tried on ma frnz system also (fedora, mint..) its not working, so the issue is not with Ubuntu. May be its with my LAN.
I am behind a proxy server and use lan connection (broadband). I manually configured it in network manager.
Can anyone suggest good reason for error. Seems to be some resolving problem...

---

### Post by piyush.neo on 2010-08-19
sorry there was a problem with my dns..change it..now working fine...

---

