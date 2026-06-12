---
title: "Python sockets issue"
date: 2010-01-31
forum: Programming Talk
---

### Post by Tahakki on 2010-01-31
Hey guys,

The following are two scripts, each sending and receiving a file. One is command-line based, and one is part of a larger GTK program.

```

import socket

eggs = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
eggs.bind(('', 2144))
eggs.listen(5)
rbuf="yes"

while 1:

    channel, data = eggs.accept()
    myFile = open('received', 'wb')
    tosend = open('/home/joel/Music/Ash/Meltdown/02 Orpheus.mp3', 'rb')
    sendstring = tosend.read()
    print data
    
    while (rbuf != ""):
        rbuf = channel.recv(4096);

        if (rbuf==""):
            break

        myFile.write(rbuf)
        myFile.flush()

    break
eggs.sendall(sendstring)
eggs.close()

```

```

            hostname = str(connectText1.get_text())
            port = int(connectText2.get_text())
            s.connect((hostname, port))
            print "Connected to " + hostname
            connect.hide()
            game.show_all()
            response = picture.run()
            if response == gtk.RESPONSE_OK:
    	        file = open(picture.get_filename(), 'rb')
                stringToSend = file.read()
                recieved = open('recieved', 'wb')
                s.sendall(stringToSend)
                game.show_all()
                rbuf = "yes"
                while (rbuf != ""):
                    rbuf = s.recv(4096);
                    if (rbuf==""):
                        break
                recieved.write(rbuf)
                recieved.flush()
                gameImage.set_from_file(recieved)
            picture.hide()
```

The first process, whereby the second script sends and the first receives, works fine. However, when the second file tries to send, it gets stuck - I believe the second script is stuck in a while loop, though I'm not sure. On exiting the program, I am told there was a broken pipe.

Help? What am I doing wrong?

---

### Post by dwhitney67 on 2010-01-31
This doesn't seem right; what are you trying to accomplish here?:
```

...
eggs.sendall(sendstring)
eggs.close()

```
Sending a message across your 'eggs' socket will not be received by the client, since it is utilizing a different socket.  Don't confuse the 'eggs' socket with the 'channel' socket, which on the client side is the 's' socket.

Thus it is channel <----> s.

P.S.  Why does your server-side have the outside while-loop?  It is unnecessary.  Or perhaps what you need is:
```

while 1:
    ...

    channel.sendall(sendstring)
    channel.close()
    break

```
Once again, the notion of having the while-loop seems superfluous.

---

### Post by Tahakki on 2010-01-31
I think I had the outside while loop in for a different reason. Changed to the following at the server end:

```
import socket

eggs = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
eggs.bind(('', 2144))
eggs.listen(5)
rbuf="yes"

channel, data = eggs.accept()
myFile = open('received', 'wb')
tosend = open('/home/joel/Music/Ash/Meltdown/02 Orpheus.mp3', 'rb')
sendstring = tosend.read()
print data

while (rbuf != ""):
    rbuf = channel.recv(4096);

    if (rbuf==""):
        break

    myFile.write(rbuf)
    myFile.flush()

channel.sendall(sendstring)
eggs.close()
```

I still get that 'Broken Pipe' error, though, at the server end. Is it an issue with the client or server?

---

### Post by dwhitney67 on 2010-01-31
> **Tahakki said:**
> I think I had the outside while loop in for a different reason. Changed to the following at the server end:

```
import socket

eggs = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
eggs.bind(('', 2144))
eggs.listen(5)
rbuf="yes"

channel, data = eggs.accept()
myFile = open('received', 'wb')
tosend = open('/home/joel/Music/Ash/Meltdown/02 Orpheus.mp3', 'rb')
sendstring = tosend.read()
print data

while (rbuf != ""):
    rbuf = channel.recv(4096);

    if (rbuf==""):
        break

    myFile.write(rbuf)
    myFile.flush()

channel.sendall(sendstring)
eggs.close()
```

I still get that 'Broken Pipe' error, though, at the server end. Is it an issue with the client or server?

You may want to wait for the client to receive the voluminous amount of data (from an mp3 file!) that you are sending before you close the server's listen socket.

Consider employing a hand-shaking protocol, where the client will notify the server once all of the data has been received.  Once the client is done, then you can have the server close its socket.

Here's something I threw together, that accomplishes something similar to your application...

Server.py:
```

import Socket

tcpServer = Socket.TCPServerSocket()
tcpServer.bind('', 9000)

if tcpServer.activityDetected():
	tcpClient = tcpServer.accept()

	while 1:
		if tcpClient.activityDetected():
			filename = tcpClient.recv(1024)

			if filename == '':
				print 'Detected activity, but nothing to read. Client disconnected?'
				break

			if filename == 'Done':
				break

			print 'Sending data for ' + filename

			file = open(filename, 'rb')
			fileData = file.read()

			tcpClient.sendall(fileData)

	tcpClient.close()
tcpServer.close()

```
Client.py:
```

import Socket

tcpClient = Socket.TCPClientSocket()

tcpClient.connect('localhost', 9000)

myMp3 = open('WaitingForTheBus.mp3', 'wb')
tcpClient.send('/tmp/WaitingForTheBus.mp3')

while 1:
	if tcpClient.activityDetected(5):
		data = tcpClient.recv(4096)

		if data == "":
			break

		myMp3.write(data)
		myMp3.flush()
	else:
		break

tcpClient.send('Done')
tcpClient.close()

```
Those two modules rely on the Socket.py module below:
```

import socket
import select
import string

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
			chunk = self.sock.recv(msgLen - bytesRcvd)

			if chunk == "": break

			bytesRcvd += len(chunk)
			msg       += chunk

			if string.find(msg, "\n"): break
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

### Post by Tahakki on 2010-01-31
Even keeping the listen socket open at the end still gives the same error.

---

### Post by dwhitney67 on 2010-01-31
The app I posted works for me; no issues whatsoever.

I did realize, however after posting my code, that the message sent to indicate the client is done is unnecessary.  When the client closes its socket, the server will be notified.

Thus if you want to experiment with the code I posted, you can remove the Send('Done') from the client, and the if-conditional statement (that checks for 'Done') & break from the server.

---

### Post by Tahakki on 2010-01-31
Sorry, I'd thought you meant that simply not closing the socket in my own program would resolve the issue.

I will give your code a try, but is this really the simplest way to do it? :P

---

### Post by dwhitney67 on 2010-01-31
> **Tahakki said:**
> 
I will give your code a try, but is this really the simplest way to do it? :P
No, the easier way to solve the problem is to fix your code such that the Server does not blow away its socket until *after* the Client has closed its socket.

Your Server should block on the recv() call; when it receives a null-string, that will be the clue that the Client has closed its socket.

---

### Post by Tahakki on 2010-01-31
So, change:

```
    if (rbuf==""):
        break
```

to

```
    if (rbuf==""):
        eggs.close()
```

?

---

### Post by dwhitney67 on 2010-01-31
I guess so.

Typical server setup:
```

# 1  open socket
# 2  bind the socket
# 3  listen on the socket
# 4  accept client connection(s)

        # 4.1  while client is connected

                # 4.1.1  receive data from client
                # 4.1.2  if data size is 0 bytes, client disconnected... break from loop
                # 4.1.3  otherwise, process data

        # 4.2  close client connection (optional)

# 5  repeat step #4 if necessary
# 6  close listen socket

```

Client setup:
```

# 1  open socket
# 2  connect to the server
# 3  send message to the server
# 4  await response from server (optional)
# 5  close socket

```
The tricky part is with the Client.  If it needs to receive data from the Server, how much will it receive?  Remember, recv() is a blocking call.  You do not want the client waiting forever to receive data; hence that is why the usage of select() is recommended.  If there is data to receive, select() will tell you so.  You can also setup select() to provide a timeout, should you never receive anything.  See my example for more details.

---

