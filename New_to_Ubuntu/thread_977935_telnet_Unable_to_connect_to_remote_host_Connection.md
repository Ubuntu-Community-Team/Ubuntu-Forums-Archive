---
title: "telnet: Unable to connect to remote host: Connection refused"
date: 2008-11-10
forum: New to Ubuntu
---

### Post by k33bz on 2008-11-10
I am trying to get firewatir installed and configured, but right now I am having problems connecting to the Localhost via telnet, ```
keebler@k33bz-mobile:~$ telnet localhost 9997
Trying 127.0.0.1...
telnet: Unable to connect to remote host: Connection refused

```

```
sudo netstat -an | grep 9997

```

shows no print out. I cant even connect via port 25. No matter what port I try to connect to I get Unable to connect to remote host: Connection refused.

What do I do?

---

### Post by k33bz on 2008-11-10
bump

---

### Post by MasterSander on 2008-11-10
are the ports opened on your router and on the host computer?

---

### Post by k33bz on 2008-11-10
how do I check that?

---

### Post by MasterSander on 2008-11-10
for the ones on your router, you need to login to it, it depends on your router how to do this and what the username and pass is. try entering 192.168.1.1 in browser or your own ip adress, try googling your router name as well

---

### Post by k33bz on 2008-11-10
I am trying to connect to my local machine, what does my router have to do with that?

---

### Post by MasterSander on 2008-11-10
it passes through there

---

### Post by k33bz on 2008-11-10
Dont make much since, but Ok, I am in there, (linksys router) I am in the area where it says port range. Is that the right area? If so I get this when I try to enable anything.```
You cannot use the Router IP, network or broadcast address
```

---

### Post by chrisod on 2008-11-10
If you have the desktop version of Ubuntu I think the telnet daemon is turned off my default, may not even be installed. Try the instructions [here ]("http://www.ubuntugeek.com/setting-up-a-telnet-server-in-ubuntu.html")

---

### Post by k33bz on 2008-11-11
still does the same thing, and I didnt see telnet in my services

---

### Post by anubhavrocks on 2008-11-11
> **k33bz said:**
> I am trying to get firewatir installed and configured, but right now I am having problems connecting to the Localhost via telnet, ```
keebler@k33bz-mobile:~$ telnet localhost 9997
Trying 127.0.0.1...
telnet: Unable to connect to remote host: Connection refused

```

```
sudo netstat -an | grep 9997

```

shows no print out. I cant even connect via port 25. No matter what port I try to connect to I get Unable to connect to remote host: Connection refused.

What do I do?

Please check if your telnet server is up and working.
I think its called "telnetd" 
Also remember to check 
 /etc/inetd.conf

---

### Post by k33bz on 2008-11-13
nothing prints out when I telnetd.  and the values were off on the /etc/inetd.conf but I changed them to be on.```
keebler@k33bz-mobile:~$ telnet localhost 25
Trying 127.0.0.1...
telnet: Unable to connect to remote host: Connection refused
keebler@k33bz-mobile:~$ telnet localhost
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
Connection closed by foreign host.
keebler@k33bz-mobile:~$ 

```

Which I use to be able to get into my local host before(with out defying a port), now I cant.

---

