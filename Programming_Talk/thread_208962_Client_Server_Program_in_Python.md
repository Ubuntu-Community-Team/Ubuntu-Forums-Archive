---
title: "Client Server Program in Python"
date: 2006-07-04
forum: Programming Talk
---

### Post by krypto_wizard on 2006-07-04
Hi,

I have the following code for a client and server which I got from a small tutorial on the web.
```

#!/ usr/bin/env python
# tms.py (SERVER)
import socket
import sys
s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
host = ''
port = int(sys.argv[1])
s.bind((host,port))
s.listen(1)
conn, addr = s.accept()
print 'client is at', addr
data = conn.recv(1000000)
data = data * 1000
z = raw_input()
conn.send(data)
conn.close()

```
```

#/ usr/bin/env python
# filename: tmc.py (CLIENT)

import socket
import sys
s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
host = int(sys.argv[1])
port = int(sys.argv[2])
s.connect((host,port))
s.send(sys.argv[3])
i = 0
while True:
    data = s.recv(1000000)
    i+=1
    if (i<5):
        print data
    if not data:
        break
    print 'received', len(data), 'bytes'
s.close()

```
Server is installed on machine 192.168.1.4 and Client is 192.168.1.2

When I start server and the server is listening I start the clinet.

I started Client using ........
```

python tmc.py 192.168.1.4 2000 abcxyz

```
where 2000 is the port number  and abcxyz is the string I pass to
server, I get the following error...
```

ValueError: invalid literal for int(): 192.168.1.4

```
How can I fix this ? I am trying to achieve the most basic level of
networking between a client and a server.

Every help is appreciated.

---

### Post by krypto_wizard on 2006-07-04
I played around and found that I was unneccesarily converting the host to int

```

host = sys.srgv[1]

```

That fixed the problem. Just writing for somebody's reference here.

---

### Post by durand on 2008-05-11
Thanks. I'm trying to program a card game with networking. Would anyone recommend good python networking tutorials?

---

### Post by pmasiar on 2008-05-11
you may want to look at [twisted](http://en.wikipedia.org/wiki/Twisted_%28software%29) framework for networked apps

---

### Post by durand on 2008-05-11
Yeah, I've heard of twisted. Its only going to be simple calls so do you know if it's light? I don't need much functionality.

---

### Post by pmasiar on 2008-05-11
twisted in not simple - it is .... twisted :-)

---

### Post by durand on 2008-05-11
Ill try and work with sockets first..I'm still very new to python.

---

