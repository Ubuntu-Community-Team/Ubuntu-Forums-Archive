---
title: "Automate a taks of clicking some button and changing the web pages automatically?"
date: 2008-06-24
forum: New to Ubuntu
---

### Post by legolas_w on 2008-06-24
Hi
thank you for reading my post.
Every night at 3 AM I should change the internet connection that my computer uses.
When I was in windows I have ppoe connections and an application which could disconnect one and connect the other connection at the given time.

Now in linux I can not find any program to create ppoe connections and then schedule another application to disconnect one and connect the other applications.

So I configured the mode itself to have two connections inside itself, one can be disabled and then the other one can be enabled to use the secondary connection information.

everynight I should goto modem administration console (a web page) and change the used connection. 

Now I am looking to make this process automatic, so I am looking for a record reply application on top of the firefox.


Thanks.

---

### Post by hyper_ch on 2008-06-24
if you restart networking
```

sudo /etc/init.d/network restart

```
will pppoe also restarted?

---

### Post by quinnten83 on 2008-06-24
Sounds like a task for cron and some scripting to me.
You've allready created the connections, and if hyper_ch is yes, than you can create a cron job to do this every night at 3.

---

### Post by hyper_ch on 2008-06-24
I have no clue about pppoe in linux, so I asked first before mentioning cron ;)

---

### Post by legolas_w on 2008-06-24
So,
If I could create two PPOE connection in Linux then Cron job can disconnect one at 3 AM and connect the other one after disconnecting the first one?

Thanks.

---

### Post by hyper_ch on 2008-06-24
you can, if you can figure out how to dis/reconnect them by the command line

---

