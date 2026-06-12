---
title: "Mysql Remote Connection Problem"
date: 2008-08-21
forum: Programming Talk
---

### Post by GunsNRoses on 2008-08-21
I have a very strange problem, for which I couldn't manage to find info anywhere. I'm trying to connect to a remote mysql server like this "mysql -u** -p -hxx.xx.xx.xx".

When I execute this command it just hangs/freezes and does nothing, no error message, it just freezes. I'm sure that the remote machine has remote access enabled, because I have connected to it from other servers (the remote machine doesn't filter ips). 

My own mysql listens to port 3306, the same as the one for the remote machine, I've commented the bind address directive in my own my.cnf. 

I'm running Ubuntu Hardy Heron, default configuration, I haven't made anything special. 

Does anyone know a solution to this problem?

---

### Post by kpatz on 2008-08-21
Try "telnet xx.xx.xx.xx 3306" (substitute the remote server's IP for the xx.xx.xx.xx) and see if it connects or fails.

Is there a firewall on your network, between your machine and the Mysql server (say, if it's on the internet somewhere)?  Maybe that firewall isn't allowing the connection.

---

### Post by GunsNRoses on 2008-08-22
Yes, I tried telnet too with the same result, it just hangs/freezes. Also I made sure that my 3306 port isn't blocked, I executed this command: "sudo iptables -A INPUT -p tcp -d 0/0 -s 0/0 -dport 3306 -j ACCEPT". 

I've installed Ubuntu with the default options and manually haven't installed a firewall on my machine, I don't know about the remote one, but I'm sure it is configured to allow remote connections. Also something strange, when I enter this "mysql -h44.44" it hangs too, although the ip isn't valid.

---

### Post by kpatz on 2008-08-22
> **GunsNRoses said:**
> Yes, I tried telnet too with the same result, it just hangs/freezes. Also I made sure that my 3306 port isn't blocked, I executed this command: "sudo iptables -A INPUT -p tcp -d 0/0 -s 0/0 -dport 3306 -j ACCEPT".Didn't you say you successfully connected to the remote box from another machine?  Where are all the machines (local and remote) located (e.g. home, work, hosting facility, etc?)

There could be a firewall on your end (if at work) that isn't allowing the connection, or it could be the remote box is behind a firewall, if it is in a work location, or even a home location behind a router.
> Also something strange, when I enter this "mysql -h44.44" it hangs too, although the ip isn't valid.That IP translates to 44.0.0.44 so it is "valid".  The client is waiting for a response from the server.  It will time out eventually but it'll appear to be hung in the meantime.

---

### Post by GunsNRoses on 2008-08-23
After doing some research, I found out that the machine allowed only a certain family of ip's, thanks a lot for your help and inside on how "44.44" was interpreted, never knew that. Thanks again. :)

---

