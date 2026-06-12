---
title: "Need Help Connecting Windows to Ubuntu"
date: 2011-11-26
forum: New to Ubuntu
---

### Post by vincej on 2011-11-26
Hi - I have downloaded Putty and installed it on my Vista machine. I have opened port 22 on my Ubuntu 11.10 client. I have installed vnc on Ubuntu. 

I have tried to follow the Putty conf instructions ( they are very cryptic !) and all I get is 'connection refused'. 

Cann someone, please point me towards an idiots guide to using Putty or an alternative approach which is easier to use ? 

Many Thanks !

---

### Post by An Sanct on 2011-11-26
edit: Port 22 is ssh, please check if the service is running by executing:

[LEFT] ```
service ssh status
```[/LEFT]

edit2: so, if you get something like "unrecognized service", then install the SSH deamon

-------------------- previous post..
Port 22 is telnet ... as far as I can recall from memory.

Is your Ubuntu box running a telnet server/service?

What are you trying to achieve?

---

### Post by d4m1r on 2011-11-26
Port 23 is telnet, port 22 is SSH.

---

### Post by An Sanct on 2011-11-26
> **d4m1r said:**
> Port 23 is telnet, port 22 is SSH.

I did see that, thats why I edited my previous post and corrected it.

---

### Post by The Cog on 2011-11-27
Connection refused normally means that there is no service listening on that port number. On the Ubuntu server, in a command-line terminal, please use this command - it lists the listening tcp ports:
```
netstat -lnt
```
You are looking for a local address of 0.0.0.0:22 or :::22. Uf they're not there, then there is no ssh server running.

The ssh service is not installed by default on Ubuntu. The package you need to install is openssh-server. You can install it with this command:
```
sudo apt-get install openssh-server
```

---

### Post by vincej on 2011-11-28
Success !!!! I have putty working - the openssh was not installed ! 

Now I have a terminal great - But I really want to share my Ubuntu desktop with  windows machine. I have enabled remote desktop sharing on Ubuntu and have instaled vncviewer on the windows machine, but again I am getting "connection refused" 

Many Many Thanks !

---

### Post by torsionbar on 2011-11-28
Did you see Cog's note about installing ssh server?  It is not installed by default.  This is the most likely source of your problem.  You need to install ssh server, and then you need to start it.

"Connection refused" is the error you'll see when ssh is either not installed, or not running.

---

### Post by The Cog on 2011-11-28
> **vincej said:**
> I have enabled remote desktop sharing on Ubuntu and have instaled vncviewer on the windows machine, but again I am getting "connection refused" 
Again, use **netstat -lnt** to see what ports are listening. The VNC server listens on 5800 or 5900 (I forget which). 

Beware the setting that says "allow connections from the internet". this actually uses uPnP to reconfigure your router and map a port to your PC. If you do this, you **will** get pwned.

---

