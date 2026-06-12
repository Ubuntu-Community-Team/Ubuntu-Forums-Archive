---
title: "Question about Python sockets"
date: 2007-05-20
forum: Programming Talk
---

### Post by Laterix on 2007-05-20
Yep, it's me again with a new python related question. I would like to pass objects over socket. I know that there is pickle() that I can use for serialization. but using socket.recv() I need to set buffersize which I can't know. I read on Python Tutorial that it is possible to use file like methods read() and write() with sockets, but I can't find any documentation about this. I'm sure that there is someone how knows how this works since sockets are pretty basic stuff after all.

EDIT: Or should I just set big buffer size and trust that it's always enough.

---

### Post by Bluetech on 2007-05-20
The socket object has a makefile() method that returns a file-like object. But I don't think that will solve your buffer problem, although I havn't tested it, so I'm not fully qualified to answer. What I do know is that putting up a big buffer and hoping it will be enough is not the way to go.
What I think you should do is come up with some sort of protocol. For example you could first send the size of the pickled file to the other side, and then send the actual file. It also adds some reliability, since you are able to know if the file was delivered completly. Of course you can't be sure the size itself was delivered successfuly, but I suppose that's already an overkill.
If this isn't some socket exercise, I suggest you look in the libraries a little, I'm sure there are many ways to do this already.

---

### Post by Laterix on 2007-05-22
> **Bluetech said:**
> 
If this isn't some socket exercise, I suggest you look in the libraries a little, I'm sure there are many ways to do this already.
Thank you for your reply. I think that I will go with this simple protocol which sends the size before object itself. This is not a an exercise, but I couldn't really find any higher level mechanisms except Pyro, but it's a bit overkill in my case.

---

### Post by Slicestrider on 2007-05-22
Hi,

I have just been doing this very thing in Python for my work. The buffer size has to be a "sensible" number in bytes like 4096 or 8192 I believe but i have not tested it with values other than this. The important thing is that you may be sending objects that are larger than the buffer size, so you need to be able to cope with this. Here is a snippet of code that I am using:

```

    client = socket.socket ( socket.AF_INET, socket.SOCK_STREAM )
    client.connect (('localhost', MY_PORT))

    m = Message("my_message_title")

    md = pickle.dumps(m)

    # Send message
    client.send(md)
    client.shutdown(socket.SHUT_WR)

    # Get response
    data = ""
    input = True

    while input:
        input = client.recv(4096)
        data += input

    ob = pickle.loads(data)
```

The While loop makes sure you keep receiving the data from the other side of the connection until it has it all. Note that the loop will run forever unless you either:

make the call

```
shutdown(socket.SHUT_WR)
```
in the application sending the information 

OR

or close the connection in the application that is sending the information.

The 
```
shutdown(socket.SHUT_WR)
```
code only shuts down half the socket, (The writing part) as it will be wanting a response. If you don't want a response you can fully close the connection.

Hope this helps :)

---

### Post by Laterix on 2007-05-22
> **Slicestrider said:**
> 
Hope this helps :)
Thanks for the tip, but I'm not sure does it fit to my requirements. I need to have socket that is open for a long time and objects are sent both directions.

---

### Post by Slicestrider on 2007-05-22
I don't know what your application is but it might be better to close the connection after every send/receive event and the open a new connection when you need to. This is what I am doing and it seems to work very well.

---

### Post by Laterix on 2007-05-23
Ok, I'm pretty close to get my simple messaging system to work. The only problem I have is with pickle. I have debug print on both sides (client and server) and they're output is shown below:

**Server**
```

Received object:
--------------------------------------------------
(imessage
Message
p1
(dp2
S'message_data'
p3
NsS'message_type'
p4
I10
sb.
--------------------------------------------------
String length: 73
--------------------------------------------------

```

**Client**
```

Sent object:
--------------------------------------------------
(imessage
Message
p1
(dp2
S'message_data'
p3
NsS'message_type'
p4
I10
sb.
--------------------------------------------------
String length: 73
--------------------------------------------------

```
So, looks pretty much same to me...

Before sending I do
```

message_buf = StringIO()
cPickle.dump(message, message_buf, 0)
self.socket_to_server.sendall(message_buf)

```
And when received
```

message = None
try:
   message = cPickle.load(message_buf)
except EOFError:
   pass
print message

```

Is this EOFError something that shouldn't happen or does it just indicate end of stream? The "print message" results to show "None", so pickling didn't go as planed.  What am I missing here?

EDIT:
I got it to work. Now I use cPickle.loads() and cPickle.dumps() -methods which operate directly on strings.

---

