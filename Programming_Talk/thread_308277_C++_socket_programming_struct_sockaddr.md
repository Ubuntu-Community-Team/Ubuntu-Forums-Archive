---
title: "C++ socket programming: struct sockaddr"
date: 2006-11-27
forum: Programming Talk
---

### Post by mucha on 2006-11-27
Hi, I've just started with c++ for real. And I'm now trying some socketprogramming.

In a function I got this:
```
struct sockaddr their_addr;
this->sockfd = accept(*sockfd, &their_addr, addrlen);
cout << their_addr.sin_addr << endl;
```

I want to get the host of the one that is connecting.
When I compile it I get these errors:
```
httpconn.cpp: In member function &#8216;bool HttpConn::approve(int*, socklen_t*)&#8217;:
httpconn.cpp:14: error: &#8216;struct sockaddr&#8217; has no member named &#8216;sin_addr&#8217;
```

Feels I've tried everything, please help :)

---

### Post by duff on 2006-11-27
sin_addr is in sockaddr_in, not sockaddr.

---

### Post by daniminas on 2006-11-28
:-k 
struct sockaddr_in 
{ 
   short int sin_family;        /* Famyly of the address*/ 
   unsigned short int sin_port; /* Port */
   struct in_addr sin_addr;     /* Network address */
   unsigned char sin_zero[8];   /* Same size of struct sockaddr */ 
};

---

### Post by mucha on 2006-11-28
Thanks, missed that little _in after :) Now it works great

---

