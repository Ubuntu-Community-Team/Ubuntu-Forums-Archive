---
title: "Setting up firewall with ufw and iptables"
date: 2015-11-18
forum: New to Ubuntu
---

### Post by bob158 on 2015-11-18
I am trying to set up a firewall with ufw and possibly iptables.

Right now the default I set up with ufw is to deny both incoming and outgoing.

I want to open some ports 80/443/53 to allow firefox to work but ubuntu doesn't seem to have application firewall so opening up a port for firefox opens it up for others to possibly use.

 I don't want other users on my LAN to be able to see or connect to me through open ports.

I'm not proficient in iptables but someone suggested I add the following code below to /etc/rc.local

 He said it would only allow connections from localhost. Will this stop other users on LAN connecting to me through open ports

```

# Set default chain policies
iptables -P INPUT DROP
iptables -P FORWARD DROP
iptables -P OUTPUT ACCEPT

# Accept on localhost
iptables -A INPUT -i lo -j ACCEPT
iptables -A OUTPUT -o lo -j ACCEPT

# Allow established sessions to receive traffic

iptables -A INPUT -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT 

```

---

### Post by Habitual on 2015-11-18
Have a look at [https://help.ubuntu.com/community/UFW](https://help.ubuntu.com/community/UFW)
specifically "Default rules" section.
You want to allow outgoing and it is perfectly safe to do so.

---

### Post by bob158 on 2015-11-18
Even if I allow outgoing how do I prevent unwanted access to the ports I am opening up for firefox. There is no application firewall so it will be open for other users on my LAN to see.

---

### Post by Habitual on 2015-11-18
all 'incoming' is being denied.
so what will they 'see'?

but it should be something like:
```
sudo ufw deny from 192.168.1.0/24 to any port <port>
```

---

### Post by bob158 on 2015-11-18
Not all. I have to open up some ports for firefox and web browsing. And I wanted to figure out if the iptables code would restrict outside access

---

### Post by ajgreeny on 2015-11-18
Is this a server machine or a "normal" desktop/laptop used for the standard jobs that most people use computers for?

If the latter it is unlikely that you really need to use a firewall, particularly if behind a router which probably supplies firewall properties as well as network connection.

Have a look at [https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2) and run some of the port tests on that site and you may find that you are already completely invisible to the outside world.

---

### Post by bob158 on 2015-11-18
I have a laptop but I have been hacked this way before by someone on the same LAN as me. Yes a router would protect you from outside world but I'm talking about other users on the same LAN. And besides I'm not behind a router just connecting straight through ethernet. 

If anyone understands what I'm trying to do and the ip tables code above and can help, it would be much appreciated.

---

### Post by KARNVORbeefRAGE on 2015-11-21
To open these ports: 80/443/53, use the ufw command like this under root
```

ufw allow 80

```
and so forth for all ports needed.

Edit: I carelessly overlooked the issue of keeping these protected, but for reference I will leave this up

---

### Post by mcduck on 2015-11-21
Why would you need to close any ports? If you don't want anyone to be able to connect to your computer, just don't run any servers.

Open port is meaningless if there's nothing listening to that port on your system.

You only need a firewall to close a port if you have a server running and you can't stop the server (pretty rare) or you need better control of the server access than what the server itself can provide (slightly more common, although most server software have very good built-in tools for controlling who's allowed to connect), or for more fine-tuned traffic control (protection against DDOS and similar tasks). Or, of course, if you don't trust the users on *your computer* and need to limit their access to outside world.

So, I agree with ajgreeny, firewall on a normal desktop machine is pretty much pointless, and often isn't even needed on a server as long as it's properly configured.

---

### Post by The Cog on 2015-11-21
I agree with ajgreeny and mcduck. Pretty-much you don't need a firewall on a desktop. 
Don't confuse incoming connections with outgoing connections. You want to allow outgoing connections from the PC, so you can access web pages, perform name lookups etc. 

As for incoming connections (which in general you do not want), unless you run a server program of some sort, then any incoming connection attempt will be told the port is closed (connection refused). 
I gather that in Windows it can be very difficult to stop lots of default-enabled services from listening for incoming network connections (for your convenience) so a firewall is pretty-much necessary, so things are different there.

---

