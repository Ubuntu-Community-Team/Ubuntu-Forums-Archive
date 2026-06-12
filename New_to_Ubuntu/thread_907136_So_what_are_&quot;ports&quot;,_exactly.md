---
title: "So what are &quot;ports&quot;, exactly?"
date: 2008-09-01
forum: New to Ubuntu
---

### Post by cpetercarter on 2008-09-01
What are the "ports" through which a computer communicates with other computers and devices? Are particular ports reserved for particular purposes, or can a computer use any port to communicate with any device? And why are there so many ports - surely 5 or 6 would do? And what does "listening at a port" mean?

---

### Post by fiddledd on 2008-09-01
You might want to have a read [here](http://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers)

---

### Post by dioltas on 2008-09-01
yes, usually particular ports are reserved for certain services,
e.g. (from memory)
Port 80 - HTTP (Internet)
Port 25 - SMTP (Mail)
Port 22 - ssh (secure shell)
Port 21 - ftp (File Transfer Protocol)
Port 20 - Telnet
Port 6667 - IRC (Internet Relay Chat)

However there's nothing to stop you using port 80 for ssh if you want etc, these are just the ports that are normally used for those services.

There are lots of programs that use different ports. There is definitly need for more than 5 or 6! Every program that accesses the Internet does so through a certain port.

If a program is listening on a certain port, it means that it is awaiting connections. For example if you were hosting a website on your computer, you would have a program (like apache web server) listening on port 80 for connections. Then when someone connected to your computer on port 80 through their browser, they would see your webpage.

---

