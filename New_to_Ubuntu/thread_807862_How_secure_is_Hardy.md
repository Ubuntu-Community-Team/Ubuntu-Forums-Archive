---
title: "How secure is Hardy?"
date: 2008-05-26
forum: New to Ubuntu
---

### Post by metasolaris on 2008-05-26
Hi,

My question is about using torrents in Hardy: please bear with me I dont know much about either.

As I understand it, one of the things that makes ubuntu much more secure viz windows is that "all the ports are closed by default". I dont really understand what this means but I assume it has something to do with data transfer.

I have just started experimenting with Transmission, Azureus and Miro and the thought struck me that using them must 'open the ports' in some way. If so are these ports only open while they are being used and close again when these applications are quit? Or once opened do they stay opened - and hence become a security risk - untill I close them myself?

I never really understood firewalls in windows so this whole area is a bit of a black hole for me but security is very important to me.

Please advise!
Thanks

meta

---

### Post by sayakb on 2008-05-26
Ubuntu has it's own firewall mechanism using IPTables that keeps the ports closed by default. If you are not an advanced user, download and use Firestarter which would monitor all ports for any sort of intrusion, making Hardy extremely secure from any exploits, attacks (or in other words, hacking attempts, sending garbage packets etc)

---

### Post by hyper_ch on 2008-05-26
Well, when networking different programs listen and speak to different ports. For example when you surf the net you make queries to port 80 (usually). So on the server with domain.com there has to be a webserver listening on port 80 because you make a request there. Upon that request the webserver then returns some information to you - which is displayed in the browser.

So ports are kind of exchange points between a server and a client.

When you run a torrent program it also listens to certain ports - because of the structure of the torrent protocol. You're normally only in danger if you don't know what's running on what port.

In windows it's different. A firewall is also used to prevent data released to the network. As you know a lot of software do have some spyware in it which will transmit "unauthorized" data back to the software producer... it's even worse when getting software from dubious sources.

As you have in linux the source code to all thise and software repositories with trusted software that does not contain spyware this kind of firewall is useless.

Bascially I wouldn't worry about a firewall until you strat running own webserver, ssh daemon, email server, ..... just for torrenting you should be fine.

Using firestarter which alters the configuration has led to more problems for the general user as no firestarter...

---

### Post by sayakb on 2008-05-26
The problems with Firestarter is that it blocks all inbound traffic. So whenever firestarter blocks something that you need, just click on the specific event and select "Allow inbound services on port"

---

### Post by kpkeerthi on 2008-05-26
> 
I have just started experimenting with Transmission, Azureus and Miro and the thought struck me that using them must 'open the ports' in some way. If so are these ports only open while they are being used and close again when these applications are quit? Or once opened do they stay opened - and hence become a security risk - untill I close them myself?

When you start transmission, it listens for incoming connections on a certain port number. If you are running a firewall, the port is still considered 'closed' because it (the firewall) blocks all incoming traffic on the port unless it is explicity instructed otherwise. So opening a port usually means allowing a port at the firewall. When you shutdown transmission, the service using the port will die, but the port is still considered 'open'. At this point, if a malevolent hacker succeeds (which is very unlikely in linux) installing a trojan in your machine, he can very well have the trojan use the port you 'open'ed for transmission and communicate with it from anywhere and likely take control of your machine. So opened ports are a threat.

To check the port numbers used by programs running in your computer and the correspong IPs they are communication to, run this command
```
netstat -antp
```

---

### Post by metasolaris on 2008-05-26
> **kpkeerthi said:**
> When you start transmission, it listens for incoming connections on a certain port number. If you are running a firewall, the port is still considered 'closed' because it (the firewall) blocks all incoming traffic on the port unless it is explicity instructed otherwise. So opening a port usually means allowing a port at the firewall. When you shutdown transmission, the service using the port will die, but the port is still considered 'open'. At this point, if a malevolent hacker succeeds (which is very unlikely in linux) installing a trojan in your machine, he can very well have the trojan use the port you 'open'ed for transmission and communicate with it from anywhere and likely take control of your machine. So opened ports are a threat.

To check the port numbers used by programs running in your computer and the correspong IPs they are communication to, run this command
```
netstat -antp
```

How do you then close the ports after you have used Transmission? Or should you use a firewall if you want to use Transmission?

---

### Post by hyper_ch on 2008-05-26
close transmission (or whatever torrent program you're using) and port is "closed"... well, actually nothing is listening on it then...

You are running a firewall already but it's not configured and does not hinder any traffic. If you install firestarter then rules will be added to it... I think it is not necessary to configure the firewall on a desktop computer. See what I've written above.

Furthermore I assume you're also in a LAN that means you're behind a router. This router also has a firewall. I think it's better to configure that firewall than on an individual machine.

---

### Post by The Cog on 2008-05-26
I'm not disagreeing with any of the above answers, but I want to add my own way of explaining.

**OPENING PORTS**:
For TCP to be able to make a connection to a host, the receiving host must have the appropriate port number "open". A port is opened by a program running on the host telling the OS that that it wants to listen to incoming calls on that port number. The OS will then accept connections on that port and tell the program whenver a connection is received. The program is then free to send/receive data over that connection. Many concurrent connections to the same port number are allowed (think of a web server on port 80 for instance). When the program exits, the port returns to the closed state - nobody listening (this answers your question about closing ports when Transmission terminates). Connection requests to "closed" ports - port numbers that have no program listening for connections on them - are rejected by the OS.

One reason Ubuntu is much more secure than Windows is that ina default install, there are no services running that listen for incomming connections. If software were perfect this wouldn't make any difference, but if a machine is accepting incoming connections for any reason, there is a possibility that a bug in that program will allow remote attackers to take control of the machine, and there have been many examples of such bugs over the years. Machines have even been compromised by exploiting bugs in their antivirus scanners that are supposed to help protect them.

Of course you have to open ports to run a server, but it makes sense to only listen on the ports that operate the services you want to be used, i.e. don't open a file sharing port unless you actually want to share files. Windows is dreadful in this regard, and offers lots of servies by default, any of which may be the next remote exploit waiting to be discovered. And always make sure your server programs are up to date, so all the known bugs have been fixed.

**FIREWALLS**
Because Windows opens so many services to the world that you don't really want to be open, it is normal to install a firewall that prevents incoming connections by dropping packets. You may want to install a firewall on Linux either because you got used to doing this on Windows and feel insecure without it, or because you want to restrict access so only chosen IP addresses can make connections. I actually run a firewall on my PC at home so that only my work IP address can reach the SSH service. Even if my SSH server has a security flaw, no-one else can exploit it.

If you have a firewall installed, the usual firewall default is to block all incoming connections, so then you have to explicitly configure it to not to block the connections you want to allow (e.g. SSH from work). Many people also call this action "opening" the port, but it should not be confused with opening the port in the OS by running a listening program. It would reduce confusion if people called it "unblocking" ports rather than "opening" ports.

Incidentaly, on Linux, all firewalls are merely front-ends to the kernel's inbuilt netfilter module which is configured by the iptables command. All firewalls issue iptables commands (they usually write scripts full of iptables commands) to do the configuration.

Unix and Linux have files hosts.allow and hosts.deny in which you can configure lists of approved remote machines. You could use this instead of a firewall, except that not all programs respect the configuration in those files (e.g. Transmission).

**NAT**
If you are behind a router that performs address translation so that for instance, your whole internal network gets translated to one internet address, then that only works for outgoing connections where the router knows which machine is making the connection. For incoming connections, the question is "Which internal machine is this connection for?" since all incoming connections are to the one public address. So you have to make some configuration that says, any incoming connections to THIS port number should be forwarded to THAT particular internal computer. This is known as "port forwarding", but just to add to the confusion sometimes also gets lumped in with the general expression of opening a port.


To successfully receive incoming calls, all three must be addressed:
* Open a port in the OS by running a program that listens for incoming connections
* Configure any firewalls not to block incoming connections to that port
* Configure any NAT routers to forward connections to the right internal machine

P.S.
**STEALTHED PORTS**
An attempt to connect to a closed port will normally result in a message from the destination computer saying "Port Unreachable" or "Connection Refused". However, if the connection request gets lost because a firewall drops it or because a NAT router doesn't know where to forward it to, then no reply will be received and the connecton attempt will eventually time out. A well known firewall seller has coined the term "stealthed" for those situations where no response is received, suggesting that is is somehow more secure than receiving a connection refusal.

---

