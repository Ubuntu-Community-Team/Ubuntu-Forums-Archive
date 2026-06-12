---
title: "Hostname Question"
date: 2012-06-27
forum: New to Ubuntu
---

### Post by Oneeyd on 2012-06-27
This is my first time setting up a Linux server, I noticed that in some configuration files like the hosts file it is looking for a domain like server1.example.com in this hosts entry "192.168.0.100   server1.example.com     server1".

Do I need to make a domain name for it? or is it just the Hostname or name of server I created when first installing linux. I named it "TestServer" so it looks like this in my hosts file "192.168.1.100 TestServer TestServer.

---

### Post by Gone fishing on 2012-06-27
For some applications such as Squid and Apache you need a fully qualified domain name so in /etc/hosts you will need a line like

192.168.1.1    myserver.mydomain.com   myserver

---

### Post by Oneeyd on 2012-06-27
Can I just make up a domain or do I actually have to register one with ICANN and all that?

---

### Post by bab1 on 2012-06-27
> **Gone fishing said:**
> For some applications such as Squid and Apache you need a fully qualified domain name so in /etc/hosts you will need a line like

192.168.1.1    myserver.mydomain.com   myserver

What applications are you referring too?  I've never run across that.  Debian has a bug that says you need a hostname other than **127.0.0.1 localhost **, but it can be just the hostname.  See my hosts file```
127.0.0.1       localhost
192.168.1.3     malibu

```

---

### Post by Oneeyd on 2012-06-27
Attempting to set up nginx, I guess I don't really need a domain name for now. I am using no-ip to set up a static ip. Can I just use that ip as the domain for now?

---

### Post by Gone fishing on 2012-06-27
Just make it up if it's on 192.168.1.1 (or similar) that is on your internal network any way.

---

### Post by Gone fishing on 2012-06-27
bab1 both Squid and Apache come to mind.

---

