---
title: "TCP/UDP port access?"
date: 2008-05-08
forum: New to Ubuntu
---

### Post by jeffinhedon on 2008-05-08
Well here we go again !
I have installed an Amateur radio prog that simulates a transceiver
and thanks to help from this forum I have it up and running.
However the program uses TCP ports 8000-8007 
and UDP ports 1-65535 inbound
How do know wether these ports are open ?
I cant see a reference to this on the forum and I cant see an item on the menu on my Linux system that indicates this
Can anyone point me in the right direction again please?:confused:

---

### Post by Monicker on 2008-05-08
A default install of Ubuntu does not block any ports.

You can use netstat to see if anything is actually listening on the tcp ports.

```
sudo netstat -anltp|grep 800
```


If the program is running and listening, you should see it listed.  UDP is a connectionless protocol, so it won't show in the above.

---

### Post by jeffinhedon on 2008-05-08
thanks Moniker
However when I applied your instruction 
Nothing happened????
Am I missing something really simple?
Perhaps more detailed instructions for me  as a newbie???:(

---

### Post by subzero316 on 2008-05-08
Try this
Install Firestarter its a firewall.
I think it will dispay the incoming and outgoing connections with port no.

```
sudo apt-get install firestarter
```

Then run that.

---

### Post by Monicker on 2008-05-08
> **subzero316 said:**
> Try this
Install Firestarter its a firewall.
I think it will dispay the incoming and outgoing connections with port no.

```
sudo apt-get install firestarter
```

Then run that.

Firestarter is not a firewall.  :)   Its a front end to iptables, which is what actually does firewalling on linux.

---

### Post by Monicker on 2008-05-08
> **jeffinhedon said:**
> thanks Moniker
However when I applied your instruction 
Nothing happened????
Am I missing something really simple?
Perhaps more detailed instructions for me  as a newbie???:(

Could you give more details about this program?  If nothing showed at all, then your program most likely was not running.

Show the output of the following:

```
sudo netstat -anltp |grep LISTEN
```



Here is what that command shows on my machine:
```

tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN     4757/mysqld
tcp        0      0 0.0.0.0:5900            0.0.0.0:*               LISTEN     5369/vino-server
tcp        0      0 0.0.0.0:44150           0.0.0.0:*               LISTEN     4620/sshd
tcp        0      0 0.0.0.0:25              0.0.0.0:*               LISTEN     4953/master

```

As you can see, several programs are listening for connections.

---

### Post by Cappy on 2008-05-08
> **Monicker said:**
> Firestarter is not a firewall.  :)   Its a front end to iptables, which is what actually does firewalling on linux.

This isn't a forum, it's the database that does the foruming.
/Score 1 Cappy

---

### Post by Monicker on 2008-05-08
> **Cappy said:**
> This isn't a forum, it's the database that does the foruming.
/Score 1 Cappy

I see your point, but sometimes it really helps know a bit about what is under the hood of some of these applications.

Somebody in another forum on this site decided to just delete the firestarter directory, without realizing that all of the iptables rules that it had created were still in effect and being applied at start up.  By doing so, he locked himself out of being able to make ANY connections to the internet.  I was able to guide him through fixing it, but he had no idea WHAT was blocking him, so he did not know where to start in fixing it.

---

### Post by Cappy on 2008-05-08
> **Monicker said:**
> I see your point, but sometimes it really helps know a bit about what is under the hood of some of these applications.

Somebody in another forum on this site decided to just delete the firestarter directory, without realizing that all of the iptables rules that it had created were still in effect and being applied at start up.  By doing so, he locked himself out of being able to make ANY connections to the internet.  I was able to guide him through fixing it, but he had no idea WHAT was blocking him, so he did not know where to start in fixing it.

Too true, I've made a similar mistake myself.

---

### Post by jeffinhedon on 2008-05-08
OK Folks
This is it
The Prog is called Hamsphere
It a transceiver simulation that allows access to the Ham bands
It connects to the Ham bands via a server

It does show only one connection!!!!!!!

Is it significant....I am using a broad band connection

tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      4983/cupsd

---

### Post by Monicker on 2008-05-08
I took a quick pick at the instructions for the app, noticed this:

*Make sure that your firewall allow TCP/UDP traffic on port 8000-8007 and all UDP ports inbound (1-65535)*

The wording suggests to me that the 8000 range ports are for outbound traffic, which would not be blocked by default on Ubuntu.  How are you connected to the Internet?  If you are behind a home router using NAT, you will have to use port forwarding for the inbound UDP ports.  If you are connected directly to the internet, then it should work without any other changes.

---

### Post by subzero316 on 2008-05-08
> **Monicker said:**
> Firestarter is not a firewall.  :)   Its a front end to iptables, which is what actually does firewalling on linux.

yea agreed...:)....but it still is the front end(gui) rite:lolflag: and you can alter the settings in a simple way...

---

