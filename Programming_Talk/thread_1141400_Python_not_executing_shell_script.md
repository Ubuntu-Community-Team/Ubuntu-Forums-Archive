---
title: "Python not executing shell script"
date: 2009-04-28
forum: Programming Talk
---

### Post by dchurch24 on 2009-04-28
Hi all,

I have a python script that listens on an IP port and executes a given command.

The commands are looked up in a MySQL database and then sent to the tcp python server. There are multiple 'servers' running on the network.

However, I have a compiled program called ADU which executes fine - in turn the ADU unit switches a relay and turns a specified device on (lamps, amplifiers etc...)

I have another usb relay that isn't an ADU one and the script to execute it is:

echo -e 'xff\x02\x01' > /dev/ttyUSB0

This works fine from terminal, but does not run from inside Python.

Ok, I thought, I'll wrap it up in a script, so I have a script called SwitchR1.sh with the command above inside it and nothing else.

It doesn't execute either?!?

The python code is:

```

import commands
import os, subprocess

class EchoRequestHandler(SocketServer.BaseRequestHandler ):
    def setup(self):
        print self.client_address, 'connected!'
        self.request.send('hi ' + str(self.client_address) + '\n')

    def run_command(self,cmd):
          #os.system(cmd)
          subprocess.call(cmd,shell=True)
          print cmd

    def handle(self):
        data = 'dummy'
        while data:
            data = self.request.recv(1024)
            self.request.send(data)
            if data.strip() == 'bye':
                return
            self.run_command(data.strip())

    def finish(self):
        print self.client_address, 'disconnected!'
        self.request.send('bye ' + str(self.client_address) + '\n')

    #server host is a tuple ('host', port)
server = SocketServer.ThreadingTCPServer(('', 50002), EchoRequestHandler)
server.serve_forever()

```

I have tried os.system(cmd) as well, as can be seen in the commented line.

The correct command prints out to the screen so I know the IP bit is working and recieving the correct command. It just doesn't execute.

I have made sure that the user running the IP listener is the same owner of the scripts too, just in case it was a permissions error.

I can send commands such as "ls -l" etc... and they execute fine.

Does anyone know why this isn't working?

---

### Post by dchurch24 on 2009-04-28
Ok, I've just changed the script to run 'ls -l' and it runs it fine, so Python is executing the script ok.

I then thought maybe it was something to do with 'echo' (clutching at straws here) and so I did 'echo "hello" - and that worked too.

So it seems it's to do with the echo to /dev/ttyUSB0 for some reason.

---

### Post by iponeverything on 2009-04-28
try su'ing to uid of the listener and trying the echo to the dev.

---

### Post by dchurch24 on 2009-04-28
Woooaaahh! Thanks for the quick reply - but I don't know how to do what you just said to do :-)

I don't suppose you could give me a quick example.

I am so close to getting all this working - this is really frustrating, it's the last 'hurdle'

---

### Post by iponeverything on 2009-04-28
```
ps auxwww|grep <name of your listener>
```

The name in the first column will be who your process is running as.  Say its "www-data" for example..

then change to that user:

```

sudo bash
su - www-data
echo -e 'xff\x02\x01' > /dev/ttyUSB0

```

If it fails, your listening process is not allowed to write to the device.

---

### Post by dchurch24 on 2009-04-28
Thanks very much for that - sadly, it works when I do that, which means that the user DOES have rights to run that command.

I'm REALLY lost now!

---

### Post by dchurch24 on 2009-04-28
I have, however, now noticed that the rx and tx lights on the USB->Serial card are flashing, which means that the script actually is executing.

It's just not switching any of the relays...yet it does when I run the script manually.

Really odd.

---

### Post by dchurch24 on 2009-04-28
Hmmm...get somewhere. slooooowwwlly.

if I send:

sock.send("echo -e '\xff\x01\x01' > /dev/ttyUSB0")

to the listener from the client, it works.

If I send:

sock.send("echo -e '\xff\x01\x00' > /dev/ttyUSB0")

Then I get the following error on the server:

----------------------------------------
('192.168.1.4', 49923) connected!
----------------------------------------
Exception happened during processing of request from ('192.168.1.4', 49923)
Traceback (most recent call last):
  File "/usr/lib/python2.5/SocketServer.py", line 464, in process_request_thread
    self.finish_request(request, client_address)
  File "/usr/lib/python2.5/SocketServer.py", line 254, in finish_request
    self.RequestHandlerClass(request, client_address, self)
  File "/usr/lib/python2.5/SocketServer.py", line 522, in __init__
    self.handle()
  File "tcpserver.py", line 22, in handle
    self.run_command(data.strip())
  File "tcpserver.py", line 12, in run_command
    subprocess.call(cmd,shell=True)
  File "/usr/lib/python2.5/subprocess.py", line 444, in call
    return Popen(*popenargs, **kwargs).wait()
  File "/usr/lib/python2.5/subprocess.py", line 594, in __init__
    errread, errwrite)
  File "/usr/lib/python2.5/subprocess.py", line 1147, in _execute_child
    raise child_exception
TypeError: execv() arg 2 must contain only strings
----------------------------------------

This is making me think that python doesn't like the ' or \ characters - do I need to escape this?

EDIT: I have tried escaping the chars, but it's still not sending the correct string to the USB device.

---

