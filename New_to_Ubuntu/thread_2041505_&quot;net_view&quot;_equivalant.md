---
title: "&quot;net view&quot; equivalant?"
date: 2012-08-12
forum: New to Ubuntu
---

### Post by joco1500 on 2012-08-12
Hello.

I just transfered from windows xp to ubuntu 12.04

it's great but i wish that it had the net view command in terminal.

can someone give me a command that will show me all the computers on a wifi network

THANK YOU!!

---

### Post by steeldriver on 2012-08-12
You can use nmap to scan all the hosts on a given network segment - it won't discriminate between wireless and wired clients though

e.g.

```
nmap -sP 192.168.1.0/24
```Run as a regular user it will just report the hosts whose interfaces are 'up' - if run with root privileges (sudo) it will try to report other info such as MAC and vendor if available

iirc nmap is not installed by default so you would need to install it from the Software Center / Package Manager / apt-get

There are other ways to get the same information e.g. via arp but I have not used those myself

---

