---
title: "Raw socket programming on Ubuntu"
date: 2007-04-29
forum: Programming Talk
---

### Post by atkt_forever on 2007-04-29
Hi

I have installed Ubuntu  Drake 6.0 under Vmware (VMware is a virtual machine installed on windows XP). I need to write a C program using raw sockets

when i execute the code:

sockd = socket(AF_INET,SOCK_RAW,IPPROTO_RAW)

i get the result: operation not supported. is it that raw sockets are not supported on Ubuntu or I need to change some parameters.

thanx atkt

---

### Post by atkt_forever on 2007-04-29
Hi I decided to post the answer to my own question to ppl. maybe it is obvious for ppl familiar wid Linux but not for me since i m using it for the first time. login as root first and then run the program that uses raw sockets. and then ur prog shud run. thanx

---

### Post by kano on 2007-04-29
Or you could use a port that's >1024.

---

### Post by amo-ej1 on 2007-04-30
@kano no that's not true, raw sockets have nothing to do with portnumbers. You'll typically use a raw socket when you're building your own IP or ethernet packets. 

When you read <i>man 7 raw</i>

```


       Only processes with an effective user ID of 0 or the CAP_NET_RAW  capa&#8208;
       bility are allowed to open raw sockets.


```

---

### Post by kano on 2007-05-01
My bad, I read that too hastily :)

---

