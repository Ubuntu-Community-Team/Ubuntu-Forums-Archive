---
title: "Instant Messaging Program in Python"
date: 2006-03-04
forum: Programming Talk
---

### Post by punkrockguy318 on 2006-03-04
Hey all you fellow Ubuntu users :)  This week I decided to program something sweet, that would make me cool.  Just kidding :p 
I put three nights or so into this program.  This is my first attempt at a real python program, a gtk2 program, an object oriented program, and my first network program, ever.  So cut me a little slack :-P  Would some of you python guys take a look at it and see what is cool and what sucks?  I'm not really planning to make a real IM replacement, as AIM is all anyone around here uses, and Jabber is the Linux of IM...  I just did this project as a learning experience. 

Here's the source: [http://punkrockguy318.no-ip.org/nimc-0.0.1.tar.gz](http://punkrockguy318.no-ip.org/nimc-0.0.1.tar.gz)

There are a couple known problems.  I'll just get them out of the way right here:
* Logout.  If you don't logout, you will be forever online.
* No status messages.  You won't really be notified if your receipient isn't online or whatever
* Not beautiful.  Remember, I did this in three nights so the interface doesn't have much love, and there aren't enough comments.
* I found out that the open/close every request thing wasn't the greatest.  A telnet like solution would be better (keep all connections open)

Could you guys give me your opinions?  Thank you!

---

### Post by majikstreet on 2006-03-05
```

Traceback (most recent call last):
  File "interface.py", line 201, in send
    response = client.Msg(nick, text)
  File "/home/majikstreet/nimc/client.py", line 62, in Msg
    msg = '%msg%'+self.cert+'%'+self.nick+'%'+to+'%'+text
TypeError: cannot concatenate 'str' and 'NoneType' objects

```
btw, if you want to look at an existing program, there's a python jabber client called gajim... anyway, this is a jabber program, right? you weren't too clear..

---

### Post by punkrockguy318 on 2006-03-05
No, this isn't a jabber program.  This is a new instant mesasging protocol.

---

### Post by punkrockguy318 on 2006-03-05
By the way, what were you doing when your received that error?

---

### Post by majikstreet on 2006-03-05
what do you mean it's a new protocol?! what host and port do I connect to? I tried connecting to jabber.ru with port 5222 and it seemed to work.. I was trying to send a message to [email]majikstreet@jabber.org[/email]

edit: oh yeah... I'm learning python + pygtk + glade too..

---

### Post by punkrockguy318 on 2006-03-05
[QUOTE=majikstreet]what do you mean it's a new protocol?! what host and port do I connect to? I tried connecting to jabber.ru with port 5222 and it seemed to work.. I was trying to send a message to [email]majikstreet@jabber.org[/email]

edit: oh yeah... I'm learning python + pygtk + glade too..[/QUOTE]

It's a new protocol... As it it's not just a client, it's a client and server.  When your on this network, you can only talk to others on this network.

By the way, I made a newer one that sucks less, check it out!

[http://punkrockguy318.no-ip.org/NIMC-0.0.3.tar.gz](http://punkrockguy318.no-ip.org/NIMC-0.0.3.tar.gz)

---

### Post by majikstreet on 2006-03-06
like who do I connect to? Someone on my network?

---

### Post by punkrockguy318 on 2006-03-06
You connect to a server.  I don't really have a dedicated server right now.  But you connect to a server, and then you can talk to other clients connected to that server.

---

### Post by engla on 2006-03-06
Neat, it works, I tried talking to myself, and I get answers back! :)

I don't know what else to say - since it's only for learning (not world domination), I suppose packaging is not that important. You could always wrap it up in distutils (python) or autotools (general) for distribution if you want to learn that too...

---

### Post by majikstreet on 2006-03-07
makes sense now..

I just tried it... awesome :D

---

