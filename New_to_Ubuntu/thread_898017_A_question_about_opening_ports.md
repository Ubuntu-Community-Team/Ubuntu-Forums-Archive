---
title: "A question about opening ports"
date: 2008-08-22
forum: New to Ubuntu
---

### Post by xusword on 2008-08-22
Hi All:

I am confused abou firewalls as I am not sure if I am doing things correctly.

Why only file sharing programs? I had to open port 6881-6889 (bittorrent default) and 51412-51414 (transmission) for transmission to use. Why didn't I have to open ports for pidgin or even firefox to use? Is it because the number of ports that a file sharing program uses are not constant?

What is the potential harm of leaving a port open when no application is using it?

hmm... never had to think about those questions when I was using windows. I guess using linux really make you think about securities...

---

### Post by iaculallad on 2008-08-22
> **xusword said:**
> Hi All:

I am confused abou firewalls as I am not sure if I am doing things correctly.

Why only file sharing programs? I had to open port 6881-6889 (bittorrent default) and 51412-51414 (transmission) for transmission to use. Why didn't I have to open ports for pidgin or even firefox to use? Is it because the number of ports that a file sharing program uses are not constant?

What is the potential harm of leaving a port open when no application is using it?

hmm... never had to think about those questions when I was using windows. I guess using linux really make you think about securities...

Actually, all ports in Ubuntu are on OPEN (Allow) state. It is only considered in use when a certain application is using it. For the file sharing ports that you had mentioned, you are to manually OPEN it on your router and not on your Ubuntu machine. Firefox usually uses the HTTP port: 80/8080 and pidgin uses 1080 I think.

---

### Post by neurostu on 2008-08-22
>  What is the potential harm of leaving a port open when no application is using it?
There isn't one.

---

### Post by jerome1232 on 2008-08-22
> **neurostu said:**
> There isn't one.

Agreed, and it's because your p2p file sharing program listens for peers trying to connect on those ports. There's no central server that all the clients talk to (hence the peer-to-peer)

Where as pidgin sends an outgoing connection to some server (which has it's ports open listening for connections) on the internet and it facilitates the communication between you and your friends.

---

### Post by Nepherte on 2008-08-23
You should also make a difference between incoming (inbound) connections and outgoing (outbound) connections.

The programs you are referring to, such as firefox and pidgin, are programs that establish an outbound connection meaning they connect to some external server (in this case a web server or an msn server for example). They are allowed by the firewall (it's the default setting) and you shouldn't be worried about it in general.

Then you have also programs for inbound connections, meaning other external computers connect to your computer. Examples of these types of programs are samba and openssh-server. The default firewall policy is also to accept these connections. On a default ubuntu install there's no service/daemon listening for inbound connections, so there is nothing to connect to. These type of connections are the ones you should be aware of. When you install openssh-server for example, there will be a daemon listening for incoming connections. The firewall will accept incoming calls, so others will be able to connect to your computer.

---

### Post by xusword on 2008-08-23
thanks for all the informations
so this is what I can understand from all your replies
Basically firewall just supervise the network traffics. There is no risk to simply opening the ports, if you don't have a malware running somewhere in your system accepting or sending out informations you are not aware of

Please correct me if I got it wrong

---

### Post by neurostu on 2008-08-24
The OS handles all In-bound and Out-bound connections. Connections are targeted via ports...  So as long as you don't have any programs listening to a specific port any connection attempts TO that port will ignored.

That being said if you have malware running on your computer then it will be able to punch through your firewall and connect OUT over a port that you might have otherwise closed... (so having or not having a firewall will make no DIFFERENCE if your computer has been compromised, at least as far as OUTBOUND connections go)

Firewalls are [i]generally/[i] more useful at the network administration level. That way a network admin can close a specific port and prevent users on the network from accepting inbound connections which could possibly open a vulnerability in the network.  Like if you don't want a user to setup a webpage hosted on a computer you can simply install a firewall and close port 80 for that user. So no matter what the user does they cannot get inbound connections.

So you really DO NOT NEED to install a firewall if you are running Ubuntu (or most other Linux Distros). You should be more concerned with keeping your login name and password secret and safe and making sure you only install programs from the ubuntu repos or from sources you KNOW you can TRUST!

---

