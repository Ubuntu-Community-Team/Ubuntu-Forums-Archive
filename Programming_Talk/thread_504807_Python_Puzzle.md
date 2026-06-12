---
title: "Python Puzzle"
date: 2007-07-19
forum: Programming Talk
---

### Post by jvc26 on 2007-07-19
Well, its not strictly a puzzle, but it is to me. I don't want a full scripted answer, I basically just want to be pointed in the right direction and given a basic idea, or where to read to get the basic idea of how to do the following. At the moment I have tried numerous approaches, using the telnetlib and trying with sockets, however - the problem::

I want to code a chat client, not a server, but a client. Basically sort of like a telnet client or basic chat client to attach to a MUD server (or a chat server), output the lines from the server line by line to the terminal (eventually to a GUI output) but at the same time allow me to input commands such as 'say "x"' or just type in a phrase, press enter and that will be sent to the server, and the server's response will be printed on the screen. I need it to print all the time (hence I was thinking about a loop, getting the data from the server and then printing via telnetlib) This worked, but I couldnt input anything without breaking the loop.

I thought sockets might give me a more flexible approach, and have tried to read up on threading  - would this allow me to do both things at once?

Thanks very much for any help you give,
Il

---

### Post by pmasiar on 2007-07-19
[twisted](http://en.wikipedia.org/wiki/Twisted_%28software%29) is one possible framework to write that. Might be more powerfull than you need tho :-)

---

### Post by smartbei on 2007-07-19
Haven't done this myself, but from what I understand you will need to use a console library like curses to make it so that you can both recieve and send at the same time. Alternately, you could try using a thread that monitors the loop getting data from the server, and having it interupt when you press a certain button - and transfer you to send-to-server mode.

---

### Post by jvc26 on 2007-07-20
Fantastic cheers for the tips, may I ask where I may find a good twisted tutorial?
Il

---

### Post by pmasiar on 2007-07-20
[http://www.google.com/search?q=twisted+tutorial](http://www.google.com/search?q=twisted+tutorial) :-)

---

### Post by jvc26 on 2007-07-22
Thankyou - I had googled it, but under a different search title, and had got some tuts which were relatively uninformative. Cheers,
Il

---

### Post by Paul Miller on 2007-07-24
If you want to develop a telnet client, Twisted is not what you want.  You certainly can develop telnet clients using Twisted, but, IMO, it's too heavyweight for such a task.

Here is a minimal example from the telnetlib documentation (certainly a lot easier to grok than Twisted!):

```

import getpass
import sys
import telnetlib

HOST = "localhost"
user = raw_input("Enter your remote account: ")
password = getpass.getpass()

tn = telnetlib.Telnet(HOST)

tn.read_until("login: ")
tn.write(user + "\n")
if password:
    tn.read_until("Password: ")
    tn.write(password + "\n")

tn.write("ls\n")
tn.write("exit\n")

print tn.read_all()

```

All it does is connect to localhost (which might fail if you're not running a telnet daemon), but it's a starting point.

---

