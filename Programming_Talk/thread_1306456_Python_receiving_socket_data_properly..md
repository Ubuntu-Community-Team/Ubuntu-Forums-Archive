---
title: "Python: receiving socket data properly."
date: 2009-10-30
forum: Programming Talk
---

### Post by briansykes on 2009-10-30
Alright i apparently have a problem in python i'm trying to make a little chat bot for my server in python and it connects and all that stuff but my server seperates it's protocol by the \n line feed character and the protocols aren't always sent within one packet so i'm trying to put all of them into a global string which i can do and filter through them one by one problem is its not working as i dont get the beginning of the protocol so here is my code:

```
def recv_data():
	global wsbuffer
	while 1:
		try:
			recv_data = client_socket.recv(RECV_BUFFER)    
		except:
			print "Server closed connection, thread exiting."
			thread.interrupt_main()
			break
		if not recv_data:
				print "Server closed connection, thread exiting."
				thread.interrupt_main()
				break
		else:
				wsbuffer = wsbuffer + str(recv_data)
				while wsbuffer.find("\n") > 0:
					i = wsbuffer.find("\n")
					newcom = wsbuffer[i -1:]
					wsbuffer = wsbuffer[i + 1:]
					processdata(newcom)
					print "Received data: ", newcom + "\n"
```
The while loop is where i begin to process the code, if anyone has any ideas it would be greatly appreciated.

---

### Post by dwhitney67 on 2009-10-30
Maybe something like this will help you:
```

class TCPSocket:
        def __init__(self, sock=None):
                if sock is None:
                        self.sock = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
                else:
                        self.sock = sock

        ...

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

```
Usage:
```

tcpClient = Socket.TCPClientSocket()

tcpClient.connect("", 9000)
tcpClient.nonBlocking()

tcpClient.send("Hello Server!\n")

if tcpClient.activityDetected(5) == True:
        response = tcpClient.recv(256)
        print response,

```

---

### Post by briansykes on 2009-10-30
would the usage not be tcpClient = TCPSocket()?

Also i assume the nonBlocking() function is a custom one that i would have to make the way i do it now is just in an if block of if __name__ == "__main__": so make a class and fill it with the send and recv functions just curious though, what is the activityDetected(5) more so the 5.  Also thanks for the reply.

Here is the "main" of my code:
```
if __name__ == "__main__":

	print "*******TCP/IP Chat client program********"
	print "Connecting to server"

	client_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
	client_socket.connect((HOST, PORT))

	print "Connected to server"

	thread.start_new_thread(recv_data,())
	thread.start_new_thread(send_data,())

	try:
		while 1:
			continue
	except:
			print "Client program quits...."
			client_socket.close()

```

---

### Post by dwhitney67 on 2009-10-30
The complete code for Socket.py
```

import socket
import select
import string


class TCPSocket:
	def __init__(self, sock=None):
		if sock is None:
			self.sock = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
		else:
			self.sock = sock

	def nonBlocking(self):
		self.sock.setblocking(0)

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

	def activityDetected(self, timeout = 0):
		ready_to_read, ready_to_write, in_error = select.select([self.sock], [], [], timeout)
		return len(ready_to_read) > 0



class TCPClientSocket(TCPSocket):
	def __init__(self, sock=None):
		TCPSocket.__init__(self, sock)

	def connect(self, host, port):
		self.sock.connect((host, port))



class TCPServerSocket(TCPSocket):
	def __init__(self, sock=None):
		TCPSocket.__init__(self, sock)

```

---

### Post by briansykes on 2009-10-30
From what i've read in the documentation for python you dont have to import the string module anymore or is it wrong because i dont have that in my code and strings work fine.  Also thank you very much for that i've apparently been doing this the wrong way, thanks for the eye opener :)

---

### Post by dwhitney67 on 2009-10-30
> **briansykes said:**
> From what i've read in the documentation for python you dont have to import the string module anymore or is it wrong because i dont have that in my code and strings work fine.  Also thank you very much for that i've apparently been doing this the wrong way, thanks for the eye opener :)

I do not keep up with the latest with Python.  For me, writing code in Python ranks up there with going to church on frigid Sunday morning.

---

### Post by briansykes on 2009-10-30
Hey, i got it to work but for some reason once i receive the initial hello from the server in the form of a colon and send client and user information i dont get anything else back the code i am using is below.

```
def main():
  global tcpClient
  tcpClient = TCPClientSocket()
  tcpClient.connect("localhost", 3001)
  tcpClient.nonBlocking()
  
  if tcpClient.activityDetected(5) == True:
    response = tcpClient.recv(256)
    processdata(response)
    print response
if __name__ == "__main__":
  main()
  raw_input("Please return to quit")
```

---

### Post by Can+~ on 2009-10-30
> **briansykes said:**
> From what i've read in the documentation for python you dont have to import the string module anymore or is it wrong because i dont have that in my code and strings work fine.  Also thank you very much for that i've apparently been doing this the wrong way, thanks for the eye opener :)

The string module was deprecated in favor of having direct string methods:

"Hello World".<method here>

> I do not keep up with the latest with Python. For me, writing code in Python ranks up there with going to church on frigid Sunday morning.

Great thing that I became atheist.

---

### Post by dwhitney67 on 2009-10-30
> **briansykes said:**
> Hey, i got it to work but for some reason once i receive the initial hello from the server in the form of a colon and send client and user information i dont get anything else back the code i am using is below.

```
def main():
  global tcpClient
  tcpClient = TCPClientSocket()
  tcpClient.connect("localhost", 3001)
  tcpClient.nonBlocking()
  
  if tcpClient.activityDetected(5) == True:
    response = tcpClient.recv(256)
    processdata(response)
    print response
if __name__ == "__main__":
  main()
  raw_input("Please return to quit")
```

Let's practice using some punctuation please!

You said you got it to "work", yet at the same time you are not satisfied with the results.

Usually the client connects to the server; then either one of them initiates the "conversation".  There may be replies from one or the other while the conversation takes place.

At what point are you having issues?

Also, why do you need a global variable in Python??  If needed, pass the object as a parameter to a function.

Also, would it not make more sense if you plan for your server and client to carry on a long conversation, that the 'activityDetected' call, and hence the 'recv' call, be encompassed in some sort of loop, perhaps a while-loop?

---

### Post by briansykes on 2009-10-30
Wow, i feel like a moron the while loop worked perfectly sorry for the confusion and thanks alot to all of you who helped me.

---

