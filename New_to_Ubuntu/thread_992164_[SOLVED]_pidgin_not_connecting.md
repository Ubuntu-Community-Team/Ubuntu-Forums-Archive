---
title: "[SOLVED] pidgin not connecting"
date: 2008-11-24
forum: New to Ubuntu
---

### Post by duruttye on 2008-11-24
Anybody noticed that from a while pidgin can't connect to yahoo messenger?

I have two other friends having the same problem. Nothing changed, first started about two weeks ago, we had to try to connect 3-4 times, to finally have a connection, then gradually it went dead.

Anybody else?

---

### Post by Het Irv on 2008-11-24
Not me, Yahoo is working fine here.

---

### Post by Keen101 on 2008-11-24
I've seen other people complain about this too.

I haven't had any problems. But, i don't use yahoo that much anymore either. But, when i do, i have no problems.

I'm going to say either yahoo has changed something with their protocol, or your router(s) keep resetting often.

---

### Post by duruttye on 2008-11-24
Any ideas how to check it out?
Is there any way to make pidgin show why it can't connect?

---

### Post by gychang on 2008-11-24
> **duruttye said:**
> Anybody noticed that from a while pidgin can't connect to yahoo messenger?

I have two other friends having the same problem. Nothing changed, first started about two weeks ago, we had to try to connect 3-4 times, to finally have a connection, then gradually it went dead.

Anybody else?

I am having the same problem, used to connect but not recently...

gychnang

---

### Post by duruttye on 2008-11-24
Well, I already said, that there are two more friends having the same problem, one of them is in the next room, using the same ISP, modem and router, the other is a few hundred miles away. So?

How can we check out where the missing piece is?

---

### Post by southernpsy on 2008-11-24
this worked for me:

[http://ubuntuforums.org/showthread.php?t=973284&highlight=pidgin+yahoo](http://ubuntuforums.org/showthread.php?t=973284&highlight=pidgin+yahoo)

---

### Post by duruttye on 2008-11-25
Watch out guys!

That works like a charm!!!

---

### Post by jimreynold2nd on 2008-11-25
Agree, I figured it out too after trying (not ping) nslookup. Coz on my computer it said more clearly that "name of service not known"
It seems like the name servers that serving scs.msg.yahoo.com are sometimes unreachable by pidgin

---

### Post by rohan.modi on 2009-10-10
Hey
i was having problem with yahoo in 9.04
but changing page server to cn.scs.msg.yahoo.com
worked for me
i was having problem with ip address  with error 5050 port forwarding not allowed
thanx  a lot

---

### Post by adhika_rexuss on 2009-10-11
> **rohan.modi said:**
> Hey
i was having problem with yahoo in 9.04
but changing page server to cn.scs.msg.yahoo.com
worked for me
i was having problem with ip address  with error 5050 port forwarding not allowed
thanx  a lot

Thanks a lot, that solved my problem connecting to yahoo :)

---

