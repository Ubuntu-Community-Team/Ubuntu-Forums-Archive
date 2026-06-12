---
title: "How can I be notified when nm connects?"
date: 2010-03-16
forum: Programming Talk
---

### Post by dav2dev on 2010-03-16
Hi all (and sorry for my bad english)
I want  that whenever networkmanager connects to the Internet, a program be run.
I suppose d-bus is the right place to do this, but i don't know how...can you please help me?

---

### Post by roccivic on 2010-03-18
No idea about d-bus. Off the top of my head, I guess you could poll:
[PHP]
#!/bin/bash
status=$( ifconfig eth0 | grep "inet addr" )
if [ -z "$status" ]; then
  echo "not connected"
else 
  echo "connected"
fi
[/PHP]

then save status to file and compare. That will tell you when a specific interface has acquired an IP address.

---

