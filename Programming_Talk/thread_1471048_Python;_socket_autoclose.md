---
title: "Python; socket autoclose"
date: 2010-05-03
forum: Programming Talk
---

### Post by Psycho.mario on 2010-05-03
I am writing a simple program that can listen or connect to a port, just like netcat does. However, my problem is that the server/client does not automatically exit or anything when the other end disconnects. Is there anyway i can check for the disconnection, so i can act on it?

Thanks

---

### Post by dwhitney67 on 2010-05-03
If you are using a TCP (stream) socket, then you should be able to deduce when the socket has been closed.  If you are using UDP, then you will not know until you try to send something (and it fails).

With TCP, *before* you ever try to receive data from a peer, you should first check if there is actually something to read.

Something like:
```

if mySocket.activityDetected():
        data = mySocket.recv(1024)

        if len(data) == 0:
                print "Peer disconnected."
        else:
                print "Got data from peer."

```
The method activityDetected is implemented as a method of the class Socket (which is homemade, not a Python construct):
```

def activityDetected(self, timeout = None):
        if timeout is None:
                ready_to_read, ready_to_write, in_error = select.select([self.sock], [], [])
        else:
                ready_to_read, ready_to_write, in_error = select.select([self.sock], [], [], timeout)

        return len(ready_to_read) > 0

```



P.S.  Here's the entire Socket.py module, which probably should be called TCPSocket.py:
```

import socket
import select
import string
from errno import EWOULDBLOCK


class TCPSocket:
        def __init__(self, sock = None):
                if sock is None:
                        self.sock = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
                else:
                        self.sock = sock

        def close(self):
                self.sock.close();

        def nonBlocking(self):
                self.sock.setblocking(0)

        def reuseAddr(self):
                self.sock.setsockopt(socket.SOL_SOCKET, socket.SO_REUSEADDR, 1)

        def sendall(self, msg):
                self.sock.sendall(msg)

        def send(self, msg):
                totalSent = 0;
                while totalSent < len(msg):
                        sent = self.sock.send(msg[totalSent:])
                        if sent == 0:
                                raise RuntimeError, "Socket Connection Broken."
                        totalSent += sent

        def recv(self, msgLen):
                msg = ""
                bytesRcvd = 0
                while bytesRcvd < msgLen:
                        try:
                                chunk = self.sock.recv(msgLen - bytesRcvd)

                                #if chunk == "": break
                                if len(chunk) == 0: break

                                bytesRcvd += len(chunk)
                                msg       += chunk

                                if string.find(msg, "\n"): break

                        except socket.error, e:
                                if e.args[0] == EWOULDBLOCK:
                                        break

                return msg

        def activityDetected(self, timeout = None):
                if timeout is None:
                        ready_to_read, ready_to_write, in_error = select.select([self.sock], [], [])
                else:
                        ready_to_read, ready_to_write, in_error = select.select([self.sock], [], [], timeout)
                return len(ready_to_read) > 0



class TCPClientSocket(TCPSocket):
        def __init__(self, sock = None):
                TCPSocket.__init__(self, sock)

        def connect(self, host, port):
                self.sock.connect((host, port))



class TCPServerSocket(TCPSocket):
        def __init__(self, sock = None):
                TCPSocket.__init__(self, sock)

        def bind(self, address, port):
                self.sock.bind((address, port))
                self.sock.listen(5)

        def accept(self):
                clientSock, clientInfo = self.sock.accept()
                return TCPClientSocket(clientSock)

```

---

### Post by Psycho.mario on 2010-05-03
I am using TCP because I haven't even got round to looking at UDP yet. 
This is what i have concerning receiving data:

```
    while 1:
        data = serverc.recv(4096)
        if not data: sys.exit()
        sys.stdout.write(data)
```
(i use sys.stdout.write(data) becuase it is running from a function inside another thread)
how could i implement what you have given me to make it exit on no data? the second line doesn't actually seem to do anything...
Sorry if i am completely wrong, i am very new to python.

Thanks

---

### Post by Psycho.mario on 2010-05-03
Because of the way i have written my program, that previous bit of code is in a function in a thread, so could i just do:
```
while serverc.activityDetected():
    count +=1
else:
    sys.exit()
```Would that work?

---

### Post by dwhitney67 on 2010-05-03
Use the keyword 'break' to exit from a loop; or alternatively set a flag.  Avoid calling exit(), for it is not a very graceful way to terminate an application.

```

while 1:
        data = socket.recv(1024)

        if len(data) == 0:
                break

        ...

```
or
```

keepRunning = True

while keepRunning:
        data = socket.recv(1024)

        if len(data) == 0:
                keepRunning = False
        else:
                ....

```

---

### Post by Psycho.mario on 2010-05-03
Ill try that, but i don't know if break will work, because its inside a thread. Ill post back with results.

Thanks

---

