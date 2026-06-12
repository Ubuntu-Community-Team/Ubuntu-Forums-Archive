---
title: "internet ports ...stupid question"
date: 2008-06-11
forum: New to Ubuntu
---

### Post by lunaluna on 2008-06-11
when a open port is used by program to connect to internet,is it allowed for only the particular program at a time or it doesn't really matter...?

---

### Post by Cypher on 2008-06-11
If the program is using classic sockets programming and binding to the port at the lowest level, the program will usually get/ask an execlusive lock. Other programs will get an error message if they attempt to open the port..

---

### Post by lunaluna on 2008-06-11
> **Cypher said:**
> If the program is using classic sockets programming and binding to the port at the lowest level, the program will usually get/ask an execlusive lock. Other programs will get an error message if they attempt to open the port..

nice so if i use ktorrent/azureus/something similar... will i have this feature? if yes how do i enable it?

---

### Post by superprash2003 on 2008-06-11
go to your torrent perferences.. and set a port number there.. and ensure you open the same ports in your router as well. [www.portforward.com](www.portforward.com)

---

### Post by lunaluna on 2008-06-12
> **superprash2003 said:**
> go to your torrent perferences.. and set a port number there.. and ensure you open the same ports in your router as well. [www.portforward.com](www.portforward.com)

ok but will the program have an exclusive lock on the port? is there a way to achieve this?

---

### Post by The Cog on 2008-06-12
Are you talking about making connections to the internet or receiving connections from the internet?

In general, a program that makes a connection **to** the internet will not specify the port number it calls out from and will get given an unused port number (typically above 1024). It must of course specify the destination port number it will connect to because this determines the service it will receive. In theory two programs could make outgoing calls from the same port number to different destinations, but I don't know of any operating system that actually allows it. But because the source port is not normally specified, may programs can make outgoing calls at once, even to the same remote host/port.

For incoming connections, a listening program (server) will nearly always specify the port number it wants to listen on. It doesn't make sense for two programs to be able to listen on the same port number - which one would the call go to? Trying to listen on a port that's already in use gets the program an address-in-use error - it can't do it.

---

### Post by lunaluna on 2008-06-12
....

---

### Post by lunaluna on 2008-06-12
> **The Cog said:**
> Are you talking about making connections to the internet or receiving connections from the internet?

In general, a program that makes a connection **to** the internet will not specify the port number it calls out from and will get given an unused port number (typically above 1024). It must of course specify the destination port number it will connect to because this determines the service it will receive. In theory two programs could make outgoing calls from the same port number to different destinations, but I don't know of any operating system that actually allows it. But because the source port is not normally specified, may programs can make outgoing calls at once, even to the same remote host/port.

For incoming connections, a listening program (server) will nearly always specify the port number it wants to listen on. It doesn't make sense for two programs to be able to listen on the same port number - which one would the call go to? Trying to listen on a port that's already in use gets the program an address-in-use error - it can't do it.

sorry i posted before seeing the post
so neither ubuntu allows a port to be used by 2 programs the same time or i have to figure this out?
as for torrents and p2p which are the right settings for downloading safe(nothing is safe of coarse but as much as we can...)?

---

### Post by jtrindle on 2008-06-12
Torrents are kind of both incoming and outgoing... there's a range of ports used by connnections coming back to the torrent "client" in addition to the port used going out to the tracker.

That said, Lunaluna, I don't think *I* understand your question enough to answer it.  Are two programs you are running which are conflicting?  Could you give a specific example?

---

### Post by lunaluna on 2008-06-12
> **jtrindle said:**
> Torrents are kind of both incoming and outgoing... there's a range of ports used by connnections coming back to the torrent "client" in addition to the port used going out to the tracker.

That said, Lunaluna, I don't think *I* understand your question enough to answer it.  Are two programs you are running which are conflicting?  Could you give a specific example?

first of all i'm not an expert so what i'm asking in simple words is can i "lock" a certain amount of ports in order to be used only by a particular program(in & out)? but only with this program?:popcorn:

(it's all about file sharing...)

---

### Post by the_doc on 2008-06-12
I don't think you can lock specific ports to specifc apps on the client because as explained previously the OS uses what's available within a certain range.  You can do this on a server, but that's different.

---

### Post by lunaluna on 2008-06-12
> **the_doc said:**
> I don't think you can lock specific ports to specifc apps on the client because as explained previously the OS uses what's available within a certain range.  You can do this on a server, but that's different.

So what's the best settings for torrents- azureus specific-regarding security?

:)

---

### Post by the_doc on 2008-06-12
I'm no expert on this.  However, I would not use a binary only client (not sure what yours is) as I wouldn't trust it, I would also be careful what other software/services I ran on the same box, in case of leaving a potential exploit.

I'm not sure what you can do in terms of port security specifically though.

---

### Post by the_doc on 2008-06-12
I've just had info from a friend of mine who knows a thing or two about torrents.  That is if you block ports on your PC you restrict the traffic of donloads from your box, if the torrent client detects this (apparently they can) they seriously throttle your download bandwidth as a form of punishment.

It would seem that a decent firewall/anti-virus combo is the best option.  Or don't use torrents!

---

