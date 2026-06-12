---
title: "Python; duplex sockets"
date: 2010-04-26
forum: Programming Talk
---

### Post by Psycho.mario on 2010-04-26
Hi,
    I am writing a python version of netcat, to practice my programming skills. I have hit a problem when sending and receiving data. Here is the code:
```
#!/usr/bin/python
import socket
import sys
#
ipname = ''
#
if len(sys.argv) == 1:
    uinput = raw_input("Cmd line: ")
    uinput = uinput.split(' ')
else:
    uinput = sys.argv[1:]
#
if "-h" in uinput:
    print """Insert Help Here"""
    sys.exit()
if "-p" in uinput:
    port = uinput[uinput.index("-p")+1]
    if not port.isdigit():
        print "Port argument not valid"
        sys.exit()
    if int(port) > 63356:
        print "Port argument not valid"
        sys.exit()
    tmp = uinput.index("-p")
    uinput.remove(port)
    uinput.remove("-p")
    port = int(port)
if "-l" in uinput:
    server = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
    server.bind((ipname, port))
    server.listen(1)
    if "-v" in uinput: print "Listening on (any) port %s" % port
    serverc, clientaddr = server.accept()
    while 1:
        data = serverc.recv(4096)
        if not data: break
        print data
        while 1:
            serverc.send(raw_input(''))
```if you run this script with the arguments "-l -p (port > 1024) -v" and then connect to it with a netcat session (which i am using for testing) e.g "nc 127.0.0.1 (chosen port)" 
After connection, the client (netcat) can send data to the server, which is shown. if the server then sends something back, the client can no longer send data, or at least it is no longer shown. (you can send data by typing something in and pressing Enter)
What is the problem here, i have a feeling it is to do with the last two while statements, but i do not know how to rectify the problem, so i can send and receive data from both server and client, as you can with netcat.

Thanks in advance

---

### Post by dwhitney67 on 2010-04-26
Examine this bit of code:
```

...
        while 1:
            serverc.send(raw_input(''))

```
How do you expect your server code to exit this while-loop?

As long as the app is stuck in the loop shown above, the server will no longer receive anything sent to it, because it will never reach the top of the outer while-loop.

---

### Post by Psycho.mario on 2010-04-26
So how can I get both loops to execute at the sametime? I would need to recv and send data at the same time. Is this a job for threading?

Thanks

---

### Post by dwhitney67 on 2010-04-26
The use of threads is a possibility; however based on the code you have provided so far, I do not know if you really need this feature.

Will your client be sending data while the server is busy collecting input from the user?  Or will your application behave similar to a chat app where a 'conversation' between two parties will take place?

---

### Post by Psycho.mario on 2010-04-26
it will be just like how netcat functions, so a chat like app with data passing backwards and forwards between client and server

---

### Post by Psycho.mario on 2010-04-27
Is this even possible in python?

Thanks

---

### Post by dwhitney67 on 2010-04-27
If you are asking about whether threads are possible, then the answer is yes.

Consider defining a main-thread (usually this is just the main entry point of the application) that will create a receiver thread and a sender thread.

Since you are receiving messages, you will need to display them somewhere.  Thus when you create your receiver thread, pass it a parameter indicating where to display the messages.  For now, just give it the standard-out stream.  Later you could augment/change this to be a GUI or whatever.

Similar for the sender; for now, just read from standard-in.  Later, perhaps read the data the user enters within a GUI.

---

### Post by Psycho.mario on 2010-04-27
Would you recommend i research and use thread (import thread) or threading (import threading)

Thanks

---

