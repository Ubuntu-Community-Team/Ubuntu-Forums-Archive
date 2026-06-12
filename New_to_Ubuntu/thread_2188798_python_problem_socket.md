---
title: "python problem socket"
date: 2013-11-19
forum: New to Ubuntu
---

### Post by sathyanarayana.pvr on 2013-11-19
In my program  knowingly i am closing my client socket and keeing small sleep in server side,after closing client socket i am sending data from server to client(closed client address)  but I am not getting any exception. I supposed to get exception as client is closed.  how to handle this situvation .


My server

mport socket
import time
import sys

#HOST = '127.0.0.1'     
PORT = 5066              # Arbitrary non-privileged port
s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
s.setsockopt(socket.SOL_SOCKET, socket.SO_KEEPALIVE, 1)
s.bind((HOST, PORT))
s.listen(1)
conn, addr = s.accept()
print 'Connected by', addr
while 1:
    data = conn.recv(1024)
    if not data: break
    print "received data is .....",data

    time.sleep(10)                     

    try:
       print "In try..."
        datalen = conn.send(data)
       print "Sent data is ...",datalen
    except:
       print "Unexpected error.......aaa...:", sys.exc_info()

conn.close()



My client 

import socket

HOST = '127.0.0.1'   

PORT = 5066              # The same port as used by the server
s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
s.setsockopt(socket.SOL_SOCKET, socket.SO_KEEPALIVE, 1)
s.connect((HOST, PORT))
s.send('Hello, world')
s.close()

---

