---
title: "Advice on inter-process communication"
date: 2012-08-10
forum: Programming Talk
---

### Post by erupter on 2012-08-10
Hello.
 
As a project for my master thesis, I'm developing a multi-robot mapping system where the robots share data.
Now since this is all simulated, i run one simulator (player/stage under  ubuntu 12.04) with multiple robots, and connect multiple processes (via  sockets) to it to control each robot.
 
If it were a real situation with real robots, I could use a TCPIP network and just use the local broadcast.
But given I'm confined to one machine, I need to devise a way to have  multiple processes (each the same, I mean only one program executed  multiple times with different command line parameters) communicate with  each other.
 
A socket system would require each process to register a different  socket, and a proxy process to be running and doing the mailing of the  messages.
It could be a thesis by itself.

Are there any available solutions I could exploit to concentrate on the real matter of my work? (the mapping)
I am proficient with C, not that much with C++ although I'm familiar with OOP (been using .NET for quite some time).

---

### Post by dwhitney67 on 2012-08-10
If you have multiple processes that need to share data, and they are all running on the same system, then shared-memory seems the way to go.  However this requires one of the processes to create the shared-memory segment, and the other processes to merely attach to it.

Your notion of using sockets is also a viable choice.  You could have a central process that functions as a data router (server).  Thus it would be responsible for creating/binding a "listen" socket that your processes (clients) could connect to.  When one of these processes issues a data message, the server would forward this data to all connected clients, unless it also supports point-to-point messaging.

---

### Post by erupter on 2012-08-10
> **dwhitney67 said:**
> If you have multiple processes that need to share data, and they are all running on the same system, then shared-memory seems the way to go.  However this requires one of the processes to create the shared-memory segment, and the other processes to merely attach to it.

Your notion of using sockets is also a viable choice.  You could have a central process that functions as a data router (server).  Thus it would be responsible for creating/binding a "listen" socket that your processes (clients) could connect to.  When one of these processes issues a data message, the server would forward this data to all connected clients, unless it also supports point-to-point messaging.

But if I have understood it correctly, the router option would mean that each process attaches via a different socket, and the router has to effectively be a router: maintain a table of connected clients, and forward each to message to every client but the sender.
I would like to avoid so much manual work if possible.

Problem with the shared memory: I'm not familiar with it.
I've been reading about it, but it seems it lacks any kind of notification.
That's to say it's plain and simple a bunch of memory that many processes can access.
Now this doesn't have any "manager" so each process should be contrived in a way to inherently avoid overriding others' memory area.
Also since there is no manager, each process should poll its own area to intercept changes.

Ideally I'm looking for a way to send "formatted" messages, an infrastructure that already provides some facilities (like forwarding, seeding, sender/receiver separation, payload agnostic, queuing, signaling,...).
Isn't there anything out there?

I've seen this done for embedded RTOSes, doesn't Linux provide anything similar?

---

### Post by dwhitney67 on 2012-08-10
> **erupter said:**
> But if I have understood it correctly, the router option would mean that each process attaches via a different socket, and the router has to effectively be a router: maintain a table of connected clients, and forward each to message to every client but the sender.
I would like to avoid so much manual work if possible.

Why?  This is the most trivial of solutions to employ.  You have a server listening for connections, say on port 12345.  Your robot controllers (client) connect to the port, and then send/receive data.  You could write the server application, in say Java or Python, in less than 50 lines of code.

> **erupter said:**
> 
Problem with the shared memory: I'm not familiar with it.
I've been reading about it, but it seems it lacks any kind of notification.

That's correct.
> **erupter said:**
> 
That's to say it's plain and simple a bunch of memory that many processes can access.

Again, that's correct.

> **erupter said:**
> 
Now this doesn't have any "manager" so each process should be contrived in a way to inherently avoid overriding others' memory area.
Also since there is no manager, each process should poll its own area to intercept changes.

The shared memory would need to be defined, similarly when one defines a structure.  You lay out where each data entity will reside; individual processes could have their own area and possibly even share a common area.

> **erupter said:**
> 
Ideally I'm looking for a way to send "formatted" messages, an infrastructure that already provides some facilities (like forwarding, seeding, sender/receiver separation, payload agnostic, queuing, signaling,...).
Isn't there anything out there?

I've seen this done for embedded RTOSes, doesn't Linux provide anything similar?
Yes; a lot of the better RTOSes are based on Unix/Linux.

Other IPC constructs available include: message queues and pipes.

---

### Post by erupter on 2012-08-10
> **dwhitney67 said:**
> Why?  This is the most trivial of solutions to employ.  You have a server listening for connections, say on port 12345.  Your robot controllers (client) connect to the port, and then send/receive data.  You could write the server application, in say Java or Python, in less than 50 lines of code.


I fail to understand how the server would identify the different clients if they connect on the same port.

> **dwhitney67 said:**
> 
Yes; a lot of the better RTOSes are based on Unix/Linux.

Other IPC constructs available include: message queues and pipes.

Exactly: I've succesfully used Semaphores/Mutex and message queues in a number of embedded project with FreeRTOS.
I'll try having a look around about queues and pipes in Linux.

---

### Post by dwhitney67 on 2012-08-10
> **erupter said:**
> I fail to understand how the server would identify the different clients if they connect on the same port.

Each client that connects to the server is afforded a unique socket.  These sockets are distinct from the socket that the server uses to listen for connections.

If you plan to support point-to-point communication, then the client will need to provide the server with an identifier attribute.  But if all you plan to do is route data to all clients, except to the one that sent data, then the task is trivial.

A simple pseudo-code implementation:
```

Thread1:

while (true)
{
    listensock = socket()
    bind(listensock)
    listen(listensock)

    client = accept(listensock)

    addClientToList(client)

    startClientMonitorThread(client)
}

Client Thread:

while (true)
{
    client = activityDetectedFromClient()
        
    data = readFromClient(client)

    sendDataToAllOtherClients(data, client)
}

```
You could limit the number of clients that can connect, and if you wish, you could just use one thread to process all clients.

The list of clients will be merely a collection of unique numbers (in C/C++) or handles in Java/Python.  The list will need to be guarded against concurrent access.

---

### Post by SledgeHammer_999 on 2012-08-10
Since you're using Linux and specifically Ubuntu you should consider using D-bus. It should do whatever you are seeking to do with inter-process messaging. Unless you want really really really fast communication between you're processes it should be ok.

---

### Post by mevun on 2012-08-10
I had a co-worker who swore by zeromq, but I've never tried it myself.  The website does even recommend building on Ubuntu. 

Basically, it provides an API to connect endpoints.  I think you can do centralized or point-to-point.  

[http://www.zeromq.org/](http://www.zeromq.org/)

---

### Post by MadCow108 on 2012-08-10
I would also advise zeromq (or something similar)
its low level enough to give you a lot of freedom to do what you want but high level enough to be very easy to use. control serverless networks are described well in their manual.
you can start with in memory sockets or local ipc sockets (unix domain sockets) and easily scale it up to internet sockets even using multicast by just changing a couple of lines.

shared memory is more useful if you really share a lot of stuff (like huge dataarrays you don't want to post over the wire) it might get a bit tedious if you just want to pass a couple of messages around.

I wouldn't be using dbus its more designed for service oriented software.

---

### Post by erupter on 2012-08-10
Thanks.
I'm having a look at zeromq, dbus and kbus.

---

