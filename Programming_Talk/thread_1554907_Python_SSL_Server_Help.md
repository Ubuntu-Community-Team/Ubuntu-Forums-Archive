---
title: "Python SSL Server Help"
date: 2010-08-17
forum: Programming Talk
---

### Post by Dudeman02379 on 2010-08-17
Im strugeling with writing an ssl enabled server in python on ubuntu.  I have quite a bit going on here and any help would be appreciated.  So here it goes.

I am trying to write a server that will allow a connection from an already existing client application and just print out whatever data is sent to is.  I do not want to change any code in the client app at all.  I just want the server to work with the existing client code.  Here is what I have written so far for the server app


```
#!/opt/python2.7/bin/python

import sys, socket, ssl
from ssl import PROTOCOL_TLSv1

#main function
bindsocket = socket.socket()
bindsocket.bind(('192.168.42.39', 9001))
bindsocket.listen(5)

while True:
    newsocket, fromaddr = bindsocket.accept()
    connstream = ssl.wrap_socket(newsocket, server_side=True, certfile='mycert.pem', keyfile='m$
    deal_with_client(connstream)

def deal_with_client(connstream):
    data = connstream.read()
    # nll data means the client is finished with us
    while data:
        if not do_something(connstream, data):
            print data
            #We'll assume do_something retrns False
            # when we're finished with client
            break
        data = constream.read()
        print data
    #finished with client
    connstream.close()
```

And here is the client app

```
#!/opt/python2.7/bin/python

import sys, socket, ssl
from ssl import PROTOCOL_TLSv1

#launcher
if sys.argv[1] == '-h':
    sys.exit("USAGE: my_client.py {ip of server}")

#main function
s = socket.socket()
ssl_sock = ssl.wrap_socket(s, ssl_version=PROTOCOL_TLSv1, ciphers='ADH-AES256-SHA')
ssl_sock.connect((sys.argv[1],9001))
#send initial packet
packet = '\x50\x4b\x0a\x00\x0b'
ssl_sock.send(packet)
#send second packet
packet = '\x05\x61\x64\x6d\x69\x6e'
ssl_sock.send(packet)
response = ssl_sock.recv(1024)
print response
s.close()
```

Now when I launch the server app it listens ok but when I launch the client app both ends throw errors.

Here is the error the server app throws

```
Traceback (most recent call last):
  File "./ssl_listener.py", line 13, in <module>
    connstream = ssl.wrap_socket(newsocket, server_side=True, certfile='mycert.pem', keyfile='mycert.pem', ssl_version=ssl.PROTOCOL_TLSv1, ciphers='ADH-AES256-SHA')
  File "/opt/python2.7/lib/python2.7/ssl.py", line 342, in wrap_socket
    ciphers=ciphers)
  File "/opt/python2.7/lib/python2.7/ssl.py", line 121, in __init__
    self.do_handshake()
  File "/opt/python2.7/lib/python2.7/ssl.py", line 281, in do_handshake
    self._sslobj.do_handshake()
ssl.SSLError: [Errno 1] _ssl.c:499: error:1408A0C1:SSL routines:SSL3_GET_CLIENT_HELLO:no shared cipher
```


And here is the error the client app throws.

```
./ssl_connect.py 192.168.42.39 dict.txt
Traceback (most recent call last):
  File "./ssl_connect.py", line 13, in <module>
    ssl_sock.connect((sys.argv[1],9001))
  File "/opt/python2.7/lib/python2.7/ssl.py", line 297, in connect
    self.do_handshake()
  File "/opt/python2.7/lib/python2.7/ssl.py", line 281, in do_handshake
    self._sslobj.do_handshake()
ssl.SSLError: [Errno 1] _ssl.c:499: error:14094410:SSL routines:SSL3_READ_BYTES:sslv3 alert handshake failure
```


Can anyone please give me a suggestion to get my server to listen correctly?  Why is complaining about the cipher?  They are both set to use the same cipher!

EDIT:
Not sure if it makes a difference or not but here is how I generated the certificate
```

openssl req -new -x509 -days 365 -nodes -out mycert.pem -keyout mycert.pem

```

---

