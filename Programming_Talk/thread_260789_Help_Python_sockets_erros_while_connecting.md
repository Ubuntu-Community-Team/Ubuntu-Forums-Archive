---
title: "Help: Python sockets erros while connecting"
date: 2006-09-19
forum: Programming Talk
---

### Post by idn on 2006-09-19
Hi,

I have started to experiment with socket programming in python, I have a simple script so far:

```

#!/usr/bin/env python


from socket import *    # import *, but we'll avoid name conflict
import sys
          

              
sock = socket(AF_INET, SOCK_STREAM)

sock.connect(("192.168.1.15", 2124))

#sock.connect(("127.0.0.1", 2124))

#sock.connect(("google.com", 80))

sock.close()

```

I can connect to google ok, but when I try to connect to my own computer using the first line I get

```

Traceback (most recent call last):
  File "./echoclient.py", line 11, in ?
    sock.connect(("192.168.1.15", 2124))
  File "<string>", line 1, in connect
socket.error: (113, 'No route to host')

```

And with the second one (127.0.0.1) I get 

```

Traceback (most recent call last):
  File "./echoclient.py", line 13, in ?
    sock.connect(("127.0.0.1", 2124))
  File "<string>", line 1, in connect
socket.error: (111, 'Connection refused')


```

Does anyone have any ideas? Is it because the ports are blocked or something? Thanks in advanced

---

### Post by nereid on 2006-09-19
Maybe there is no entry for your PC in your hostfile (/etc/hosts)?

---

### Post by idn on 2006-09-19
I am not familiar with the purpose of this file, but here  it is :)

127.0.0.1       localhost
127.0.1.1       idn-laptop

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

---

### Post by mentok on 2006-09-19
This may be a silly question, but do you have a server of some kind running on your computer on port 2124?

---

### Post by nereid on 2006-09-20
You need the hostfile to resolve 127.0.0.1 to localhost. Without this entry you PC can't connect to localhost.

---

### Post by dabear on 2006-09-20
Hi, on the server-script you should make sure that you use socket.gethostbyname() as the first param to yoursocket.bind() instead, so that the socket would be visible outside of your computer.

Also, make sure that port 2124 is accessible and not blocked by a router or firewall

---

### Post by idn on 2006-10-09
Hi

I am stil having a lot of trouble with this, and still havent figured it out, need to for uni :(

I have tried the ideas above and nothing, is it an ubuntu problem or a python one? I now have a frsh install of edgy as well, same thing

---

