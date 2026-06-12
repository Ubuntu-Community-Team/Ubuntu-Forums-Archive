---
title: "Internet Question"
date: 2008-09-25
forum: New to Ubuntu
---

### Post by jamelb on 2008-09-25
what happens from the time when you type in a web address ([www.yahoo.com](www.yahoo.com)) and hit enter, to the time when the page comes back up and is displayed to you?

---

### Post by perlluver on 2008-09-25
> **jamelb said:**
> what happens from the time when you type in a web address ([www.yahoo.com](www.yahoo.com)) and hit enter, to the time when the page comes back up and is displayed to you?

Well, it sends a request to the website, letting it know that you are trying to display it, then it send a request back letting you know it is active or down, then it transfers the data, to you.  Here is more info: [http://dev.cofind.net/tcpip/webbrowserclickstory.html](http://dev.cofind.net/tcpip/webbrowserclickstory.html)

---

### Post by DGortze380 on 2008-09-25
> **jamelb said:**
> what happens from the time when you type in a web address ([www.yahoo.com](www.yahoo.com)) and hit enter, to the time when the page comes back up and is displayed to you?

That's a much bigger question than I think you realize. This is a good place to start:
 [http://en.wikipedia.org/wiki/TCP/IP](http://en.wikipedia.org/wiki/TCP/IP)
[http://en.wikipedia.org/wiki/OSI_model](http://en.wikipedia.org/wiki/OSI_model)

It involves a number of protocols, networking layers, servers (DNS, web, and others), switches, routers, the list goes on and on and on...

The VERY basic explanation, is that you (through a large number of steps) tell the server I'm here, I want 'this' information, the server response, (actually relatively quickly, considering there are again a large number of steps), and sends you the information you want.

The 'time' between when you hit enter and when it shows up on your screen depends on EVERYTHING from the type of browser you use, to the speed of your machine/ISP, where the serve is, how it's connected, the speed and specs of the server, the connection protocol... again, the list goes on and on.

Start with that TCP/IP page if you decide you're still interested, and read through the Networking forum here.

---

### Post by lisati on 2008-09-25
[http://dev.cofind.net/tcpip/webbrowseroverview.html](http://dev.cofind.net/tcpip/webbrowseroverview.html) might be slightly easier to follow.

The steps include: 
[LIST=1]
[*]look up name of website at a "DNS server"to locate the computer which "hosts" the web site (the names of the website e.g. [www.yahoo.com](www.yahoo.com) are for people's benefit, the computers find it easier to use an "IP address")
[*]send request for info to the computer with the website
[*]computer with website processes the request
[*]computer with website sends back information to your computer
[*]your computer's browser checks the information it gest back, and hopefully shows something interesting on the screen
[/LIST]

This is a bit of a simplification: there's usually a bit of to-ing and fro-ing, and the process can involve several computers, depending on who is connected to what.

---

### Post by billgoldberg on 2008-09-25
When people ask me that question (happened 1 time, lol) I keep it simple.

I say, your computer asks the server that website is running on to see page x.

The server tells your pc it's ok.

Then your browser downloads the page.

---

### Post by patrickballeux on 2008-09-25
The easiest answer is:

* You press enter
* You wait
* It shows


This is what is happening for you...  :guitar:

But as already mentionned, this is a simple question that has a complex answer...  Read the links already provided.

---

### Post by hopkinsjeni on 2008-09-26
> **jamelb said:**
> what happens from the time when you type in a web address ([www.yahoo.com](www.yahoo.com)) and hit enter, to the time when the page comes back up and is displayed to you?

Are you having a problem with Yahoo, or do you just want to know how the webpage gets to your computer? I can't tell from your question.

---

### Post by Sycron on 2008-09-26
Well I can virtually touch the yahoo server in miliseconds, while pshihicaly in ages or never ever.

---

### Post by j.bunce on 2008-09-26
Okay, this is an example of what could happen. This will be most likely be completely different in your set up, and only covers a high level view of the basics. Please note that this only deals with the network side of things, and not what your browser is doing, i.e any of the programming language, function calls etc.

1) [www.yahoo.co.uk](www.yahoo.co.uk) is requested in the browser.
2) computer looks in it's local DNS cache to see if it knows the IP address for [www.yahoo.co.uk](www.yahoo.co.uk)
2) if not, it will send out an ARP request on the local network to map the IP address of the DNS server learnt via DHCP to a MAC address
3) once recieved, computer will send a DNS request on either UDP port 69 or TCP port 69 and request an A record for [www.yahoo.co.uk](www.yahoo.co.uk) from the local DNS server
4) if the DNS server does not know the IP address of the host [www.yahoo.co.uk](www.yahoo.co.uk), it will forward it to a higher level name server that may know. This continues until it reaches a root name server. This is known as recursive querying.
5) the DNS sends a reply, and the host now has an A record for [www.yahoo.co.uk](www.yahoo.co.uk) (87.248.120.129). 
6) if the host is unaware of the MAC address of the default gateway on the subnet(again possibly learnt via DHCP), it will send an ARP request for this, as the default gateway is the place on the network that is used to get out of the local network, and onto different networks.
7) next it will send a TCP Synchronize (SYN) message on TCP port 80 (http) in the direction of the default gateway, source 10.10.10.1:random destination 87.248.120.129:80.
8 ) if the default gateway is also a NAT server, translations will be performed here too.
9) the host waits for a TCP SYN-ACK message from the webserver. When recieved it will send another SYN message. This is the TCP 3 way handshake, used for establishing communication.
10) data transfer can now commence.

As I said earlier, this only an overview of what is happening...there is no mention of routing protocols, proxy-arp, what NAT actually does, and all the other stuff that happens. I've only mentioned what the services do, not really how they do it. There should be enough terms in there though to start wikipedia/googling about. Have a good look at TCP/IP.

Cheers,
Jake

---

### Post by hopkinsjeni on 2008-09-26
Good answer Buncey!

---

