---
title: "VNC Based on XMPP p2p"
date: 2008-02-26
forum: Programming Talk
---

### Post by Naveen Chandran on 2008-02-26
I am trying to modify an existing vnc client so as to perform NAT Traversal automatically and no other complex configurations like port forwarding etc..

I tried with telepathy project with Empathy IM and got it working with stream tubes...

.. But I am trying to create a client which can connect to any machine with vnc over xmpp..

Is it possible for direct client to client ... it can be also like one client acting as server and other acting as a client during connection.. I gone through 
[www.xmpp.org/extensions/xep-0166.html](www.xmpp.org/extensions/xep-0166.html)

but could not find implementations like what I expected like I give an IP address and port no. of server the communication goes over xmpp and gets connected...

Any Ideas? :(

---

### Post by gpothier on 2008-04-07
Hi, I would also love to have VNC over Jabber, or actually anything that permits to share my desktop with an IM contact by just clicking a button.
I stumbled upon that page today: [http://cass.no-ip.com/~cassidy/blog/index.php/post/2007/06/05/Stream-tubes-a-new-generation-of-tubes](http://cass.no-ip.com/~cassidy/blog/index.php/post/2007/06/05/Stream-tubes-a-new-generation-of-tubes)
Maybe it is of interest to you,
REgards,
g

---

### Post by zen-walker on 2009-05-12
I came across your post while googling for "XMPP vnc".

There is a windoze application that utilize XMPP to perform NAT Traversal to connect a remote VNC server and a VNC client.

It would be nice if this is ported to GNU/Linux. What is very interesting with this application is that it used the Gtalk account to initiate the connection.

It have embedded TightVNC client/server but it could used the local VNC application installed on the local machine.

This might help your project and the Linux world would benefit from it.

[http://www.gbridge.com/](http://www.gbridge.com/)

---

