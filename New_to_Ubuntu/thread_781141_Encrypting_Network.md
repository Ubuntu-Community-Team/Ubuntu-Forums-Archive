---
title: "Encrypting Network"
date: 2008-05-04
forum: New to Ubuntu
---

### Post by KHAnet on 2008-05-04
I was wondering if there was anyway in ubuntu to encrypt anything and everything that associates with my network.  all incoming and outgoing connections for total anonymous websurfing, downloading, anything etc.  thanks in advance.

---

### Post by njparton on 2008-05-06
You could probably encrypt everything on a LAN by using SSH, but over an internet connection the server at the other end would not offer such a connection.
 
Over the net, SSH is only used in specific circumstances such as banking etc.
 
Look into tor for secure surfing (I'm not sure if that's windows only or not?).

---

### Post by phr0ze on 2008-05-06
Look up 'TOR'. I don't have specifics for Ubuntu but I'm sure it's out there. This is the closest answer.

Any time you use encryption, the other end needs to understand that encryption. Thats why this is not a easy thing to do. 

You can turn on any encryption you want, but the party you are trying to talk to will not understand. get it?

---

### Post by timcredible on 2008-05-06
yeah, tor will work for linux.

---

### Post by Monicker on 2008-05-06
One thing to be aware of about Tor.  Traffic must be unencrypted at the exit node in order for the final destination to understand it.   The exit node will not know your origination, but if you have any passwords and such which are not encrypted before entering the tor network, they will be visible at the exit node.  Anyone running an exit node can still sniff the traffic.


Tor does have some overhead, and you will often see a major increase in latency because you could be routed through Tor nodes all over the world.


This all covered at the Tor web site - [http://www.torproject.org/]("http://www.torproject.org/")

---

### Post by KHAnet on 2008-05-06
Thanks for all your answers everyone.  The reason i ask this is because i believe my ISP is throttling my p2p applications and I need a solution for them to not be able to see that is p2p traffic coming from my ip address. Any thoughts on that?

---

### Post by njparton on 2008-05-07
Most bittorrent clients now offer encryption if that's that you're using.

Also try switching the default port it's using to something random like 30111.

---

### Post by phr0ze on 2008-05-07
Don't use TOR for bit torrent. You should have let us know the real problem upfront. There are tons of other sites with solutions to this problem because it affects any OS using BT. Try DSLReports.com. There are newer P2P technologies as well, you should look at wikipedia for anonymous and/or encrypted p2p.

---

