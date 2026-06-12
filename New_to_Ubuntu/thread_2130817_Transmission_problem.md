---
title: "Transmission problem"
date: 2013-03-30
forum: New to Ubuntu
---

### Post by Carnivorum on 2013-03-30
Bs'd

I installed transmission, and when I try downloading a torrent, transmission doesn't start, and I can't get it to start.  

What to do about that?

---

### Post by sudodus on 2013-03-30
Well, there are many companies that don't want you to connect to the [removed]

*Edit*: Check if you can download a linux distro with Transmission.

---

### Post by Carnivorum on 2013-03-30
> **sudodus said:**
> Well, there are many companies that don't want you to connect to the [removed] ...

*Edit*: Check if you can download a linux distro with Transmission.

Bs'd

On my other comp it works just fine...

---

### Post by sudodus on 2013-03-30
I guess your two computers sit in the same LAN (behind a router).

Transmission works for me in 12.04 LTS (but I don't connect to the pirate bay). Maybe you can check if there are any differences in the settings.

There could also be some difference in the security settings of the two computers.

---

### Post by Carnivorum on 2013-03-30
Bs'd

I looked at transmission, and he says that he uses port 51413.  When tested, he says that that port is closed.    A few others I tried are also closed. 

I'm using 12.04

---

### Post by sudodus on 2013-03-30
Have you set your firewall with ufw or gufw?

---

### Post by sudodus on 2013-03-30
When I have Transmission running, I can see that the port 51413 is in LISTEN state with the command
```
sudo netstat -lp --inet
```

---

### Post by Carnivorum on 2013-03-30
> **sudodus said:**
> Have you set your firewall with ufw or gufw?

Bs'd

I've never set a firewall

---

### Post by Carnivorum on 2013-03-30
> **sudodus said:**
> When I have Transmission running, I can see that the port 51413 is in LISTEN state with the command
```
sudo netstat -lp --inet
```

Bs'd

Used that command, but no difference.

---

### Post by sudodus on 2013-03-30
Then I don't know :-(

I had expected that you had closed that port.

---

