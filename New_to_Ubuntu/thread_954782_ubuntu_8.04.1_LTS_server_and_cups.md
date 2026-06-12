---
title: "ubuntu 8.04.1 LTS server and cups"
date: 2008-10-21
forum: New to Ubuntu
---

### Post by prt7u on 2008-10-21
Howdy,

I have a machine that is running ubuntu 8.04.1 LTS Server.  On that machine
I want to be able to print to a few networked printers here at work.  I can
do this on the machine I have running ubuntu 8.04.1 (Desktop) by having cups installed and setting up the printer via a web browser port 631.

What packages do I need to install on the "server" that will enable the printing as on the "desktop"?  I don't want the "server" to be a print server, just a client.

TIA,

Pete

---

### Post by blesbok on 2008-10-22
i'm probably out of my depth here, but have you tried administering CUPS?
point your browser to localhost:631 and start with the "add printer" tab. do that for each printer.

sorry, i reread your post and this advice is not relevant

---

### Post by Nepherte on 2008-10-22
As blesbok already mentioned, CUPS has its own printer manager in the form of a web page. You should be able to access that web page from another computer in the network by browsing to [http://ipaddress-of-your-server:631/](http://ipaddress-of-your-server:631/)

---

