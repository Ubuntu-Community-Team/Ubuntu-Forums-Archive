---
title: "Python Socket Problem"
date: 2010-12-06
forum: Programming Talk
---

### Post by 23Andrew on 2010-12-06
So, uh. My first post. I converted from Windows about a week ago, and have been doing some Python programming. I have been testing Pygame and Socket, by attempting a "simple" online game. However, I have had some problems in early stages.

The client sends data to the (currently very primitive) server, which then echo's the data to the client(s in the future.)

The (VERY condensed) Client.py looks like:

```

import socket

s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
s.connect(('localhost',50000))

while 1
  pos = (320, 240, 0)
  state= (0, 0, 0) #Just some variables in the game

  stingToSend = contract(pos, state) #Converts the digits into a string to send to the server, with numbers separated by ampersands. "320&240&0&0&0&0"
  try:
    self.s.send(stringToSend)
    print stringToSend, "Sent to ", self.s
  except socket.error, e: 
    print stringToSend, "Not sent"

  try:
    gotString = s.recv(1024)
    print interpret(gotString) , "Recieved"  #Converts the string to a list of numbers.
  except socket.error, e: 
    print "Not recieved"

```

The (condensed) server code is:

```

import socket, sys
host = ''
port = 50000
backlog = 5
size = 1024
s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
s.bind((host,port))
s.listen(backlog)
while 1:
    client, address = s.accept()
    data = client.recv(size)
    if data:
      print data, "Recieved"
    client.close() 

```

Yes, that is mainly copied off a tutorial (Bits I have added, such as the ability to terminate it, have been omitted)

The output in the terminal is:
Client
```

320&240&0&0&0&0 Sent
['320', '240', '0', '0', '0', '0'] Recieved
320&240&0&0&0&0 Sent
[''] Recieved
320&240&0&0&0&0 Not sent
[''] Recieved
320&240&0&0&0&0 Not sent
[''] Recieved
320&240&0&0&0&0 Not sent
[''] Recieved
320&240&0&0&0&0 Not sent
[''] Recieved
320&240&0&0&0&0 Not sent
[''] Recieved
etc....

```

And the server:
```

320&240&0&0&0&0 Recieved

```

So I have two questions.
1. Why did the second chunk of data get sent, but not received by the server?
2. Why didn't the 3rd + chunks get sent to the server?

They are probably really obvious answers, as this is really my first experiment with Socket. 

Any help appreciated.

Thanks
-Andrew

---

### Post by dwhitney67 on 2010-12-06
> I have a similar problem... I built a rocket that will take me to the moon, but for the life of it, I cannot seem to walk from here to the kitchen.

If I only had a penny for every time I've heard something similar to this.

@ the OP.. why can't you put together a simple scenario where a client application repeatedly sends the message "Hello" to a server application?  Consider adding a number to the message that serves as a counter for how many messages have been sent.  Thus you can be assured that each and every message is delivered.

Now, seriously, to answer your question, I will ask you a straightforward question... why is your server setup to receive only one message from the client, then close the client connection, BEFORE going back in the loop to accept the connection of another client?

You are closing the client connection right after the first/only message is received (I can't fathom why), and then you await another connection.

Your client app on the other hand, only attempts to establish a connection one time, then in a while-loop, sends boat loads of messages, even though after the very first one, the connection is closed (by the server), and hence the failures.

Sort out what you want your client and server to do, and if you still have issues, then get back to us here at the forum with your additional questions.

---

