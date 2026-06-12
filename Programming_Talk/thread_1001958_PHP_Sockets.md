---
title: "PHP Sockets"
date: 2008-12-04
forum: Programming Talk
---

### Post by ponto18 on 2008-12-04
Hi everyone...

I have this college project where i want to communicate between an application written in ANSI C and a php web page.
I have a struct with 3 int type variables that i want to send to the web page.
It works fine between my ANSI C server and ANSI C client, but there are no strutures in php so i've used a class instead, but the php socket only accepts strings...anyone can help me?

My deadline is approaching...

---

### Post by ponto18 on 2008-12-04
Hi everyone...

I have this college project where i want to communicate between an application written in ANSI C and a php web page.
I have a struct with 3 int type variables that i want to send to the web page.
It works fine between my ANSI C server and ANSI C client, but there are no strutures in php so i've used a class instead, but the php socket only accepts strings...can anyone help me?

My deadline is approaching...

---

### Post by dwhitney67 on 2008-12-04
I don't know anything specific about PHP sockets, but if I were you, I would consider serializing the data within your class so that it is in essence an array of characters (a string).  Your array will be 12 bytes long (4 bytes for each int value).

I've only perused through a PHP book once, and that was almost 5 months ago; thus I am not sure if it is easy to de-serialize on the PHP end.

Btw, you did not mention if the data is being sent from PHP to the C server, or the other way around.

---

### Post by bapoumba on 2008-12-04
Threads merged and closed. We do not allow help on homework, sorry.

---

