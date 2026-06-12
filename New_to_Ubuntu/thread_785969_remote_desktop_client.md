---
title: "remote desktop client"
date: 2008-05-07
forum: New to Ubuntu
---

### Post by Matt26 on 2008-05-07
is there a remote desktop client available for ubuntu 8.04 that uses a  secure connection for remote access and allows you to configure it so it automatically connects to a remote host when ubuntu starts?  thanks.

---

### Post by superprash2003 on 2008-05-07
remote desktop client as in a client for windows remote desktop?otherwise vncviewer is already present in ubuntu.. go to the terminal and type vncviewer 192.168.1.10:0  this will open the vnc server at 192.168.1.10 .. so you could install vnc there.. if the server is the ubuntu remote desktop then you could enable it there and connect...

---

### Post by Matt26 on 2008-05-07
> **superprash2003 said:**
> remote desktop client as in a client for windows remote desktop?otherwise vncviewer is already present in ubuntu.. go to the terminal and type vncviewer 192.168.1.10:0  this will open the vnc server at 192.168.1.10 .. so you could install vnc there.. if the server is the ubuntu remote desktop then you could enable it there and connect...

yes it is for connecting to a windows PC- i have read that VNC is not a secure client (passes data back and forth unencrypted)?  is there a way to lunch vnc from the desktop?  do you need to have a client/listening agent on the windows system being connected to in order for vnc to work?

---

