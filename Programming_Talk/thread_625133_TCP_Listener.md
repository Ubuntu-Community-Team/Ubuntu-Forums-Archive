---
title: "TCP Listener"
date: 2007-11-27
forum: Programming Talk
---

### Post by rbarr2007 on 2007-11-27
Hi

Coming from a .Net background I have a Multi-threaded TCP listener that monitors TCP traffic from GPS devices that connect via GPRS and puts the position data into a SQL Server Database.

I am now trying to figure out which direction I need to go in order to do the whole thing with with Linux instead.

The devices connect to an IP address and port on TCP and then pass positions. These positions need to be stored in a database for later analysis.

I have used the tcpreen and tcplisten utilities to test, but what is the best way to monitor the ports I select and take the data forwarded to those ports into a MySQL database for example. 

I tried figuring this out myself but I feel that I need a push in the right direction. Especially in terms of security, encryption etc.

Any help with which direction I should be looking at would be appreciated.

---

### Post by DuneSoldier on 2007-11-27
Since you come from a .NET background, have you checked out [Mono]("http://www.mono-project.com/Main_Page")? I ported some simple applications I'd written for school to Linux with it. Basically all that it took was replaces the WinForms with GTK#.

However the last time I touched .NET I was working with 1.1

---

### Post by dwhitney67 on 2007-11-28
Ethereal is probably the best choice for monitoring TCP traffic; and it's open source software.

Alternatively, you could write your own TCP listener that opens port A, for the GPS devices to connect to, and then forward the data to port B, which is where the data normally would go.  This simulates the MITM (man in the middle) concept.  Aside from forwarding the TCP data, whatever else you do with it is up to you.

If the data you are trying to intercept is encrypted, then you might have trouble interpreting it, unless you know the algorithm and the key used to encrypt the data.

---

### Post by supirman on 2007-11-28
I think the previous poster confused your intentions.  It seems as though you're wanting to write a "data position listening" server on a given ip/port.  To start writing a server, I'll point you to [ Beej's Guide to Network Programming ]("http://www.beej.us/guide/bgnet/").  

You'll obviously want to write a server which will listen on the specified port for connections from devices.  When a device connects, you accept it and read the incoming data.  You can then dump the data into a database pretty easily.  You should be able to do this in most languages.  Some people like python, some people like C, and so on.  

Certainly, start with Beej's guide for info on how you'd typically write a networked server.  

If you'd like more info, I'd be happy to assist.

---

### Post by dwhitney67 on 2007-11-29
It appears that the OP is MIA.  Who knows what he/she/it really wanted to know.

---

