---
title: "Data exchange between processes"
date: 2008-08-23
forum: Programming Talk
---

### Post by alxlabs on 2008-08-23
I have one host process running under the root and several client processes running under different user accounts. What are the options to exchange the data between host process and client ones? 
One thing I came with is to implement kind of server listening to some port (i.e. 4444 etc) but whole thing will be limited to one machine only so I don't see too much sense implementing a network server...What are the other options?

---

### Post by jinksys on 2008-08-23
Have you looked at DBUS?

[http://www.freedesktop.org/wiki/Software/dbus](http://www.freedesktop.org/wiki/Software/dbus)

---

### Post by dwhitney67 on 2008-08-24
> **jinksys said:**
> Have you looked at DBUS?

[http://www.freedesktop.org/wiki/Software/dbus](http://www.freedesktop.org/wiki/Software/dbus)
This suggestion could be overkill for the needs specified by the OP.  The reason for this opinion:
*... The low-level libdbus reference implementation has no required dependencies; the bus daemon's only *required* dependency is an XML parser (either libxml or expat)*

If processes running on the same system need to communicate with each other to share data, viable options include (but are not limited to):
[LIST]
[*]Shared Memory
[*]Message Queues
[*]Pipes
[*]TCP
[*]UDP
[*]Files
[/LIST]
Of course, a "protocol" between the two processes needs to be defined.  XML is one such protocol, but is overkill for processes running on the same system.  Transmitting binary data is much more efficient than sending ASCII data.

I just finished working on a project where a "bonehead" used XML and files to relay data from one process to another... on the same system!  Everything would have been a lot easier if TCP were used.

---

### Post by jinksys on 2008-08-24
> **dwhitney67 said:**
> This suggestion could be overkill for the needs specified by the OP.  The reason for this opinion:
*... The low-level libdbus reference implementation has no required dependencies; the bus daemon's only *required* dependency is an XML parser (either libxml or expat)*

The daemon's configuration files are in XML.

> 
Transmitting binary data is much more efficient than sending ASCII data.


Couldn't agree more.

*D-Bus is low-overhead because it uses a binary protocol, and does not have to convert to and from a text format such as XML.* [ SOURCE ](http://dbus.freedesktop.org/doc/dbus-specification.html)

---

