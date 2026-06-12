---
title: "Python TCP Server: error: (104, 'Connection reset by peer')"
date: 2009-04-29
forum: Programming Talk
---

### Post by dchurch24 on 2009-04-29
Hi all,

I have a TCP server I have written in Python, it sits and listens on multiple machines for commands that turn relay switches on and off.

In this instance I have the relays wired out to buttons on a remote control (it no longer looks like a remote control) that turns power sockets on and off, so I can control the lights, amlifiers, doors etc.... in my house without wires.

Every now and then - about 30% of the time the following error is thrown, causing the command just sent to it to not get executed and fail.

If it does fail, it leaves the last command running - which in this case is a down button press on a remote control - the lights, say, will go on or off, but the remote will continue to tell the power socket to power up or down wasting the battery.

If I am in a different room when I set this off I won't see that has happened and the batteries will run down in no time.

I cannot for the life of me see a way around it.


```

Exception happened during processing of request from ('192.168.1.15', 2854)
Traceback (most recent call last):
    self.finish_request(request, client_address)
  File "/usr/lib/python2.5/SocketServer.py", line 464, in process_request_thread
----------------------------------------
Exception happened during processing of request from ('192.168.1.15', 2856)
Traceback (most recent call last):
  File "/usr/lib/python2.5/SocketServer.py", line 464, in process_request_thread
    self.finish_request(request, client_address)
    self.finish_request(request, client_address)
  File "/usr/lib/python2.5/SocketServer.py", line 254, in finish_request
    self.RequestHandlerClass(request, client_address, self)
  File "/usr/lib/python2.5/SocketServer.py", line 254, in finish_request
  File "/usr/lib/python2.5/SocketServer.py", line 522, in __init__
    self.handle()
  File "tcpserver.py", line 31, in handle
    data = self.request.recv(1024)
    self.RequestHandlerClass(request, client_address, self)
error: (104, 'Connection reset by peer')
----------------------------------------
  File "/usr/lib/python2.5/SocketServer.py", line 522, in __init__
    self.handle()
  File "tcpserver.py", line 31, in handle
  File "/usr/lib/python2.5/SocketServer.py", line 254, in finish_request
    self.RequestHandlerClass(request, client_address, self)
    data = self.request.recv(1024)
  File "/usr/lib/python2.5/SocketServer.py", line 522, in __init__
error: (104, 'Connection reset by peer')
    self.handle()
----------------------------------------
  File "tcpserver.py", line 31, in handle
    data = self.request.recv(1024)
error: (104, 'Connection reset by peer')


```


The Python TCP Server:

```

import SocketServer
import commands
import os, subprocess
import time

class EchoRequestHandler(SocketServer.BaseRequestHandler ):
    def setup(self):
        print self.client_address, 'connected!'
        self.request.send('hi ' + str(self.client_address) + '\n')
        time.sleep(0.2)

    def run_command(self,cmd):
          if  cmd=="switch_1_on":
            # switch relay 1 on, wait 1 second (for remote) then turn off.
            os.system("echo -e '\xff\x01\x01' > /dev/ttyUSB0")
            time.sleep(1)
            #s='/bin/echo -e "\\xff\\x01\\x00" > /dev/ttyUSB0'             
            os.system(s)
          if  cmd=="switch_1_off":
            # switch relay 2 on, wait 1 second (for remote) then turn off.
            s='/bin/echo -e "\\xff\\x02\\x01" > /dev/ttyUSB0'
            os.system(s)
            time.sleep(1)
            s='/bin/echo -e "\\xff\\x02\\x00" > /dev/ttyUSB0'
            os.system(s)
          print s

    def handle(self):
        data = 'dummy'
        while data:
            data = self.request.recv(1024)
            time.sleep(0.2)
            self.request.send(data)
            if data.strip() == 'bye':
                return
            self.run_command(data.strip())

    def finish(self):
        time.sleep(0.2)
        print self.client_address, 'disconnected!'
        self.request.send('bye ' + str(self.client_address) + '\n')

    #server host is a tuple ('host', port)
server = SocketServer.ThreadingTCPServer(('', 50002), EchoRequestHandler)
server.serve_forever()



```

Is anyone able to see what I'm doing wrong, or even a workaround for the error so that the last command gets executed?

---

