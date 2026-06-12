---
title: "[Python] What ports are open?"
date: 2011-05-14
forum: Programming Talk
---

### Post by ki4jgt on 2011-05-14
I have a program I'm writing which uses sockets. I don't want my users to have to open ports on their firewalls, so what ports should I use? It's an IMing program. Connections will be coming from different IP addresses and not the same ones all the time.

---

### Post by doas777 on 2011-05-14
> **ki4jgt said:**
> I have a program I'm writing which uses sockets. I don't want my users to have to open ports on their firewalls, so what ports should I use? It's an IMing program. Connections will be coming from different IP addresses and not the same ones all the time.
well, it depends on how the connections between clients and servers (is this C/S or pure P2P?) are set up. if you create a connection from one peer directly to another, you will need to open a port. connections initiated from the inside of most firewalls can pass through, and recieve responses to that connection. note that it is the connection that can recieve replies, not the port that the connection happens to be on.

most comercial routers are configured to assume the user has no services accessible to the outside and will thus block all packets coming in that are not associated with an existing connection (one that is presumably initiated from the inside). there aren't usually any open ports for unsolicited connections, unless  you specify a DMZ, a task more tricky and dangerous than opening a port.

I'm no pro with sockets (done a little in a  few langagues) but it seems that using a server to broker the connection would be best. at application start, establish a connection with the server, and use it as an io stream. all the clients can initiate their own outbound connection to the server, and the server can use those connections to route messages to each client. I believe most major IM clients work this way. just a thought.

---

### Post by ki4jgt on 2011-05-14
> **doas777 said:**
> well, it depends on how the connections between clients and servers (is this C/S or pure P2P?) are set up. if you create a connection from one peer directly to another, you will need to open a port. connections initiated from the inside of most firewalls can pass through, and recieve responses to that connection. note that it is the connection that can recieve replies, not the port that the connection happens to be on.

most comercial routers are configured to assume the user has no services accessible to the outside and will thus block all packets coming in that are not associated with an existing connection (one that is presumably initiated from the inside). there aren't usually any open ports for unsolicited connections, unless  you specify a DMZ, a task more tricky and dangerous than opening a port.

I'm no pro with sockets (done a little in a  few langagues) but it seems that using a server to broker the connection would be best. at application start, establish a connection with the server, and use it as an io stream. all the clients can initiate their own outbound connection to the server, and the server can use those connections to route messages to each client. I believe most major IM clients work this way. just a thought.

Every client is the server. The entire network is going to pass and receive traffic. Basically every person will be part of the server.

---

### Post by doas777 on 2011-05-14
> **ki4jgt said:**
> Every client is the server. The entire network is going to pass and receive traffic. Basically every person will be part of the server.
so full P2P huh?

unfortunately all p2p applications require opening ports to receive unsolicited messages from peers. you can send messages easily but no one can recieve them, nor can you receive theirs without a port that you can send to with a listener associated.

---

### Post by ki4jgt on 2011-05-14
> **doas777 said:**
> so full P2P huh?

unfortunately all p2p applications require opening ports to receive unsolicited messages from peers. you can send messages easily but no one can recieve them, nor can you receive theirs without a port that you can send to with a listener associated.

How come Frostwire doesn't require you to open ports or Bittorrent? They never have for me anyway.

---

### Post by doas777 on 2011-05-14
> **ki4jgt said:**
> How come Frostwire doesn't require you to open ports or Bittorrent? They never have for me anyway.
check out the section "Design" here:
[http://en.wikipedia.org/wiki/Gnutella](http://en.wikipedia.org/wiki/Gnutella)

gnutella attempts to converge a web of communication partners that starts with a list of persistent nodes maintained by the service provider. there are as the wiki describes, a number of ways to pull it off, but they are all pretty advanced, and very customized. either way you end up with a potential chicken-egg scenario where you cannot connect to anyone unless you can connect to someone. for an IM system this could lead to crippling latency lag, and discoverability issues for users.

---

### Post by ki4jgt on 2011-05-14
> **doas777 said:**
> check out the section "Design" here:
[http://en.wikipedia.org/wiki/Gnutella](http://en.wikipedia.org/wiki/Gnutella)

gnutella attempts to converge a web of communication partners that starts with a list of persistent nodes maintained by the service provider. there are as the wiki describes, a number of ways to pull it off, but they are all pretty advanced, and very customized. either way you end up with a potential chicken-egg scenario where you cannot connect to anyone unless you can connect to someone. for an IM system this could lead to crippling latency lag, and discoverability issues for users.

How bad of a lag and latency issues are we talking? WOW, this was almost exactly how I was setting mine up. I'm just facing one problem right now, How to get rid of old information. Basically it would just bounce around in the network forever. I've thought of creating servers which discard all the information sent to them, but then my users would have problems. :-( Have any ideas?

---

### Post by StephenF on 2011-05-14
> **ki4jgt said:**
> How bad of a lag and latency issues are we talking? WOW, this was almost exactly how I was setting mine up. I'm just facing one problem right now, How to get rid of old information. Basically it would just bounce around in the network forever. I've thought of creating servers which discard all the information sent to them, but then my users would have problems. :-( Have any ideas?
Set a time to live value. First hand info has the TTL to its highest value like 255 then each time it is passed to another peer the value on the passed information drops by one and when it falls to zero that information is discarded. In addition have peers erode those TTL values on a schedule.

You probably also want this since it can dynamically configure your NAT in your router.

[http://en.wikipedia.org/wiki/UPnP](http://en.wikipedia.org/wiki/UPnP)

---

### Post by doas777 on 2011-05-14
> **ki4jgt said:**
> How bad of a lag and latency issues are we talking? WOW, this was almost exactly how I was setting mine up. I'm just facing one problem right now, How to get rid of old information. Basically it would just bounce around in the network forever. I've thought of creating servers which discard all the information sent to them, but then my users would have problems. :-( Have any ideas?

heres a little more info on gnutella, that may be useful:
[http://ntrg.cs.tcd.ie/undergrad/4ba2.02-03/p5.html](http://ntrg.cs.tcd.ie/undergrad/4ba2.02-03/p5.html)

check out the section on firewalls and the one on Limitations of the protocol.

in terms of your ttl issue (Stephen nailed it on that one), were you planning on daisy-chaining the peers (each peer knows one other, that only one other peer knows), or forming a web with redundant pathways? if redundant, how were you planning on determining the best path from peer to peer? 

  the latency will be a factor of "closely" connected any given pair  of peers is. if you have a web of peers, then determining and using an optimal route from source to dest is your best way to get a snappy communication. if you are daisy-chaining, then the best bet would be to chain them together based on physical locality, so you aren't routing messages to a guy in Minnesota through a node in New Zealand.

---

### Post by ki4jgt on 2011-05-14
> **doas777 said:**
> heres a little more info on gnutella, that may be useful:
[http://ntrg.cs.tcd.ie/undergrad/4ba2.02-03/p5.html](http://ntrg.cs.tcd.ie/undergrad/4ba2.02-03/p5.html)

check out the section on firewalls and the one on Limitations of the protocol.

in terms of your ttl issue (Stephen nailed it on that one), were you planning on daisy-chaining the peers (each peer knows one other, that only one other peer knows), or forming a web with redundant pathways? if redundant, how were you planning on determining the best path from peer to peer? 

  the latency will be a factor of "closely" connected any given pair  of peers is. if you have a web of peers, then determining and using an optimal route from source to dest is your best way to get a snappy communication. if you are daisy-chaining, then the best bet would be to chain them together based on physical locality, so you aren't routing messages to a guy in Minnesota through a node in New Zealand.

I was planning on creating levels based on how long the node had been connected to the network. 5 levels total. Each level would have a different task in the network. The initial message would travel as it does over normal IP. It would get routed up to level 5 and then it would come back down from level 5 and hit it's destination. But the farther up in levels you are the longer you must leave the program running, thus, the higher up in levels, the fewer clients there will be on that particular level.
Thus the higher up in levels you are, the bigger the chance you get your message. But theoretically, everyone will get their message because every level is connected to both the level above and below it.

EDIT: Should I thread this or do it process by process? I have it working process by process but don't know if it would be better to do it with threading. If I do it by threading, it will create a bottleneck effect. But process by process will prevent this (The way I have it setup) I don't know if it will slow it down or not though, this is my problem.

---

### Post by doas777 on 2011-05-14
> **ki4jgt said:**
> I was planning on creating levels based on how long the node had been connected to the network. 5 levels total. Each level would have a different task in the network. The initial message would travel as it does over normal IP. It would get routed up to level 5 and then it would come back down from level 5 and hit it's destination. But the farther up in levels you are the longer you must leave the program running, thus, the higher up in levels, the fewer clients there will be on that particular level.
Thus the higher up in levels you are, the bigger the chance you get your message. But theoretically, everyone will get their message because every level is connected to both the level above and below it.

EDIT: Should I thread this or do it process by process? I have it working process by process but don't know if it would be better to do it with threading. If I do it by threading, it will create a bottleneck effect. But process by process will prevent this (The way I have it setup) I don't know if it will slow it down or not though, this is my problem.

ahh, a mesh. very neat. It sounds like you have everything worked out. 

in terms of threading, yes, I would do threads for a couple reasons. first, network operations just scream asynchronicity, because the thread will spin until the response is received, and if it is running on the mainthread, it locks your GUI, etc. my thought is that every connection should run on its own thread, and run the request/response streams for that connection synchronously within the thread. each thread can then asynchronously notify the mainthread upon completion of a network operation. 
second, threads share information a lot better/easier than processes do, so its easier to coordinate their operations.

---

### Post by ki4jgt on 2011-05-14
> **doas777 said:**
> ahh, a mesh. very neat. It sounds like you have everything worked out. 

in terms of threading, yes, I would do threads for a couple reasons. first, network operations just scream asynchronicity, because the thread will spin until the response is received, and if it is running on the mainthread, it locks your GUI, etc. my thought is that every connection should run on its own thread, and run the request/response streams for that connection synchronously within the thread. each thread can then asynchronously notify the mainthread upon completion of a network operation. 
second, threads share information a lot better/easier than processes do, so its easier to coordinate their operations.

I haven't read up on threading so this may take a bit to figure out, but I'm planning to have this up and running as well as an initial server on a DDNS address. In a couple of months. I want to keep the system open for modification. Basically the reason I did this is because there are not really any open sourced (modern) chatting platforms for Linux. And what is open, requires a server to run. Now everyone can create their own GUI which will allow them chat with the protocol they prefer. Without having to serve anything. I do however think I'm going to leave this as just a Python module and allow the users to create their own GUIs. Well, I'm reading up on Twisted right now.

---

### Post by slavik on 2011-05-14
> **doas777 said:**
> ...
most comercial routers are configured to assume the user has no services accessible to the outside and will thus block all packets coming in that are not associated with an existing connection (one that is presumably initiated from the inside). there aren't usually any open ports for unsolicited connections, unless  you specify a DMZ, a task more tricky and dangerous than opening a port.
...

A router has 2 ports, that's it. Consumer level "routers" are not really really just routers. They are NAT devices with a DHCP server and a built in switch.

Firewalls in these devices are more of a side-effect. Since the NAT device receiving a packet to itself doesn't know where it needs to actually go (since it assumes that there are multiple devices behind it), it will drop/reject the packet. This is why you set up port forwarding to tell it to send all traffic (specifying TCP/UDP/both) what IP it should be redirected to.

DMZ is easier to set up than individual ports. Since proper port opening (talking Linux firewall or a commercial dedicated firewall (Cisco ASA)) require more arguments beyond the IP address to funnel everything it doesn't know where to send it to.

---

### Post by ki4jgt on 2011-05-15
Now, I've stumped another toe :-( IPv6. I didn't read anything on the Sockets module until just now. I've basically been building my entire program on ideas I've found scattered around the web. Are they going to get rid of IPv4? I know my program will have to be IPv6 compatible, but do I need to include v4? Or both?

Now that I've quite mumbling, do I need both of them or just one? Do ISPs translate them for you? Yeah that's the question I was driving at.

---

### Post by doas777 on 2011-05-15
> **ki4jgt said:**
> Now, I've stumped another toe :-( IPv6. I didn't read anything on the Sockets module until just now. I've basically been building my entire program on ideas I've found scattered around the web. Are they going to get rid of IPv4? I know my program will have to be IPv6 compatible, but do I need to include v4? Or both?

Now that I've quite mumbling, do I need both of them or just one? Do ISPs translate them for you? Yeah that's the question I was driving at.
theoretically, the sockets layer should insulate your code from the IP details of your communication, but there may be newer objects and methods that are required to work with both. 

I really hate to do this, but check out these search results. looks like some research may be in order: [http://www.google.com/search?q=sockets+and+ipv6](http://www.google.com/search?q=sockets+and+ipv6)

---

