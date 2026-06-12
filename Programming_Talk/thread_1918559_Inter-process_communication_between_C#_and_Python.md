---
title: "Inter-process communication between C# and Python?"
date: 2012-02-01
forum: Programming Talk
---

### Post by Kimm on 2012-02-01
Hey guys!

I am developing an application using a server/client structure, where I have a C# application running as the server which recieves queries from Python scripts (the client), processes the data and returns a reply.

Problem is finding some way to reliably pass information between the processes! The idea with the structure is for the python script to be able to launch and connect to any number of servers and query them independently. Essentially, its a simulation software, where the server takes care of all the data and the script may pass data between the servers.

It also needs to be cross-platform, as I want to make the software available for Linux, Windows as well as Mac OS X in the end.

I tried reading and writing to text-files, but this seems slow and not very reliable!

In the end, what I want is for the script to ask the server a question, then do nothing until the server replies.

Any and all suggestions would be helpfull! ^^

---

### Post by Tony Flury on 2012-02-01
If possible use named pipes - or can you use a shared memory segment between server and client (not seen a library that supports  shared memory map in Python but that does not mean it does not exist).

---

### Post by Kimm on 2012-02-01
I've been developing a terrible headache trying to wrap my head around cross-platform named pipes in Python. I decided to use TCP instead, so the server listens on localhost and the client starts the server with a specific port rather than the name of a pipe or file.

So far, this is quite a bit faster than using File IO and it opens up the possibility of extending the software later for user over multiple computers!

Thanks anyway :)

---

### Post by MadCow108 on 2012-02-01
I would not use raw tcp sockets, but instead abstractions on top of that.
it will save you a lot of work and headaches (+ its often faster)

one example would be zeromq, which is sockets + message queues but not much more (only very few builtin devices),
zeromq e.g. allows you to not care much about queueing and you can easily change between tcp sockets, unix file sockets, in memory sockets, and pgm sockets.
It is designed to scale from local machines to clusters of thousands of machines and there are bindings for pretty much all languages.

a bit higher level would be ace, spread, rapidmq or qpid which give you a bunch of devices and other nice features like builtin authentification stuff.

---

### Post by Kimm on 2012-02-02
What could be the issues of using raw TCP? Currently both the server and the scripts run in a single thread (getting everything right is more important than speed in this case)

---

### Post by Tony Flury on 2012-02-02
> **Kimm said:**
> What could be the issues of using raw TCP? Currently both the server and the scripts run in a single thread (getting everything right is more important than speed in this case)

Using raw TCP means that you have to, at some level, worry about queueing messages, handling receipt (or failure) of messages etc, and you have handle unexpected disconnections etc. Using a layer on top (like MadCow108 suggested) means that your code does not have to worry about anything like that - you just read the next message from the queue - if there is one - and your code only has to handle things like the queue being empty. 

Communication models like TCP are layered for a reason - you keep functionality together in each layer, each layer adding a new level of behaviour that builds on the previous.

---

### Post by Kimm on 2012-02-15
Thanks for the help guys!

I did try to implement some types of IPC other than pure TCP but in the end I realized that this approach was far to slow for what I wanted to do (I had to leave the computer running overnight to process data in one simulation, it took 6 hours and 24 minutes). So I decided to learn more Python and rewrite the whole thing as a set of python classes (that I now have other issues with since I dont know much Python). Already, I cut down the 6 and half hours to 40 minutes, so its a clear improvement! :)

Now to start a thread about my Python issues...

---

