---
title: "python help: multiple network loops of different types?"
date: 2007-04-25
forum: Programming Talk
---

### Post by mem on 2007-04-25
NOTE: this is long and somewhat complicated, but please give it a chance. I'm really hoping someone can shed some light on this for me, as i've all but given up...

I'm working on a little app that i think would be really cool for system admins in certain environments, but I can’t seem to nail down the program logic on how to do this network communication. Everyone i've asked says its way over their head so I'm really looking for some advice at this point on how to handle this.

I’m trying to have a client-server type thing, but I’m trying to accomplish the following with each:

(user) -> (web server/webapp or gui program) <-----> (server) <----> (client machines)

- server(s?): broadcasts its ip&port for local machines to see where the server is and what its listening on. The broadcast would be UDP, and would continuously go out every 30 seconds or something.
- client: listens for broadcasts from server (which contain the ip & port of the server). When/if it gets it, it sends a reply to the server. The client would constantly have to check for new servers broadcasting.
- server: adds client to a list of all clients it has heard back from.
- server: continuously checks for TCP connections from clients with data.
- client: sends data periodically to the server (every 5 seconds) on the main TCP connection.
- server: also listens on another port for connections from ‘users’. (was thinking about using xml-rpc or something along those lines)
- users: use some web based solution (hosted on some apache web server) or gui program that connects to my server (wanted to try and do this with some php/ajax type thing), authenticates (my server application has mysql backend connections to store users and other stuff about the client machines), and then issues ‘commands’
- server: gets ‘command’ from the user and sends it to the appropriate client machine over the TCP connection.
- client: along with sending data every 5 seconds, also listens for commands from the server.
- client: receives cmd from the server and sends reply.
- server: processes reply and sends formatted info back to the user

Looking at it now… no wonder no one can help me. I realize this would require a ton of threads, and I’d like to keep it as simple as possible, hopefully using SocketServer if I can.

I think i'd need three loops on the server:
1. some type of socket interaction to get UDP broadcasts
2. some type of listener to handle incoming client (machine) connections
3. another listener to handle incoming user connections

and 2 on the client:
1. a broadcast UDP listener
2. a listener for commands from the server

Anyone have any suggestions on how to handle this? My thoughts so far for the server where to:
launch a thread that initiates each network loop
in the two listener threads, launch more threads for the incoming connection, and use locks to handle all the connections.

I'm really hurting for some advice here :(

---

### Post by amohanty on 2007-04-25
I am wondering as to what you are trying to do here?

A couple of things come to mind:

1. System monitoring and/or remote commands
2. Cluster management

For both those things, a lot of specialized tools exist that can be hooked together to do what you want.

For e.g. instead of this fancy tcp/udp mixed environment think about the following:

1. User interacts throug web app (as you mentioned)
2. web app is made of two components:
  a. client manager
  b. client commmander (so to speak)

Now you could implement 2a. a couple of different ways. 
1. would be what you suggested above. in that scenario the best place to start would be twisted
    [http://twistedmatrix.com/trac/](http://twistedmatrix.com/trac/) whic provides abstractions for a lot of the low level stuff you want to do, or you could look at the bittorent source code for a peer discovery implementation, or you could look up udp broadcast examples on aspn's recipes website
2. you could follow the 'heartbeat' route and let all clients tell the server periodically if they are alive. any client that misses two hearbeats is considered dead, or something of that sort. since the server already hosts web apps, the clients could just to an HTTP get on a special url with query args to do that.

Regarding multiple servers, if you have to have them, instead of dumping some sort of a single 'client-gateway' in between which would be easier to implement as a first cut, you could potentially implement some sort of server-peer-state-replication, ie, server a is alive and all clients have been bootstrapped with server a. server b comes up and knows about server a and simply asks it for the list of clients (which of course now knows about server b - a naive routing table kind of thing) and lets them know about its own existence. A more explicit solution is always more easier. You could of course go the full blown peer-discovery route, but I think if the number of servers and the number of clients is large enough and heartbeats are important, you could be spending a lot of network bandwidth just sending out stuff on broadcast.

The client commander could be something as simple as a python wrapper around 'ssh user@hostname command' just to make sure that the user that logged into server is allowed to do stuff on the client. or it could be something fancier like another web service on the client. if you dont like web servers, you could create a very simple socket server on the client to recieve line based input for commands and auth info. ASPN has some examples as to how to set up socket server in python. Here too twisted has some cool modules to do that.

HTH
AM

---

### Post by mem on 2007-04-25
ignoring the zero-config aspect, in order to use any solution would both the server and the client have to spawn two socket objects? one for sending and one for receiving at each end? if so, how can you do that while still having a primary program loop?

by 'loop' i'm referring to:
on the client where every 5 seconds it sends out info,
while elsewhere its also waiting for remote commands to come in so it can reply to them separately

and on the server where it constantly listens for the periodic data from the client,
while elsewhere listening for connections from 'users' on another port where it'll accept commands and respond back to the user.

PS. I'm going to try and check out twisted today at work, but i wanted to get a reply in before i left just in case i couldn't find time today.

---

### Post by mem on 2007-04-25
You know... thinking about it some more now, i guess i could just send an 'update' command to every client from the server every 5 seconds, that way the server just has to listen for commands?

but then how would i keep track of the clients from the server, to know who to send the 'update' commands too? and still how can i have multiple running loops that on the server:
for every client in a list:
wait N seconds and send 'update' command'
wait for response, and update in local DB

loop, waiting for incoming connection from 'users' on a different socket/port.
process incoming commands and reply back to 'user'

---

### Post by amohanty on 2007-04-25
> ignoring the zero-config aspect, 

If you think about it a bit, nothing is really zero config. :)

> in order to use any solution would both the server and the client have to spawn two socket objects? one for sending and one for receiving at each end? if so, how can you do that while still having a primary program loop?

I would suggest not dealing with sockets directly at all. Try using apache or some other web server to deal with the 'waiting' and the 'looping'. Basically, use the web server thats already on the server to service users, and to let clients 'register' themeselves with the server. Also let server 'peers' talk to each other via the same server, different urls. 

Similarly let web servers on clients do the 'waiting' and 'looping'. ie server sends commands to a url via an HTTP GET/POST and client sends server the response back. If its a long running task, you might want to use some sort of async communication, for e.g.:

server hits [http://client1/do?cmd=some_command&arg1=a1&cmdId=a1234](http://client1/do?cmd=some_command&arg1=a1&cmdId=a1234)
once client is done, client hits [http://server1/done?client=cl1&cmdid=a1234](http://server1/done?client=cl1&cmdid=a1234)

In that scenario, you dont have to worry about different sockets/ports, etc just different urls or to be even more strict, different virtual servers on apache. 

This should work in most cases, but depending on what you are actually trying to do, you just may have to use sockets and in that scenario, read up on the poll objects in the select module.

HTH
AM

---

