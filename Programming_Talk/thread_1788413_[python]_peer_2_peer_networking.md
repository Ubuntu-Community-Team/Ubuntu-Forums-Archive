---
title: "[python] peer 2 peer networking"
date: 2011-06-22
forum: Programming Talk
---

### Post by Dhiraj Thakur(Invincible) on 2011-06-22
hey all ..i wanted to write an simple p2p app for simple chat between two computers in LAN....so for that i need some great tutorials or books that specifically target p2p programming in python....plz recommend some tuts or books...

and are thre any libraries in python which target p2p programming..like sockets...

---

### Post by DangerOnTheRanger on 2011-06-22
Well, there's Entangled ([http://entangled.sf.net]("http://entangled.sf.net/")) and Khashmir ([http://khashmir.sf.net]("http://khashmir.sf.net/")) (both are Python libraries), but I don't think either of those are maintained any more.

---

### Post by Dhiraj Thakur(Invincible) on 2011-06-22
> **DangerOnTheRanger said:**
> Well, there's Entangled ([http://entangled.sf.net]("http://entangled.sf.net/")) and Khashmir ([http://khashmir.sf.net]("http://khashmir.sf.net/")) (both are Python libraries), but I don't think either of those are maintained any more.
I meant inbuilt libraries....

---

### Post by DangerOnTheRanger on 2011-06-22
I don't think Python has any built-in P2P networking libraries.

---

### Post by Dhiraj Thakur(Invincible) on 2011-06-23
help me guys i just want to write a simple chat program.....

---

### Post by NovaAesa on 2011-06-23
If the chat is between only 2 computers, you could just take the easy way out, open a set of sockets and simply send the text straight through them.

---

### Post by BkkBonanza on 2011-06-23
I'm sure you googled but in case you didn't think of that - this useful link pops right up - stackoverflow often has really useful stuff, worth bookmarking.

[http://stackoverflow.com/questions/963305/python-library-framework-for-writing-p2p-applications](http://stackoverflow.com/questions/963305/python-library-framework-for-writing-p2p-applications)

I think if I were doing this I'd probably just write my own code as the basic idea isn't too hard. Open a listening socket and for each incoming connection spawn a thread to handle any commands received. What you actually do depends on your protocol you design.

Then your main loop might handle local stuff and spawn connections to other peers. Part of your protocol would result in a table of peers built from the incoming commands, eg. HELLO CMD comes and says "Hey I'm a peer" causes a new entry in peer table. You would want some kind of auth test of course so not just anyone can chat. You might look at the POP protocol as an example as it relates to sending messages, though I think even simpler can be done.

---

### Post by Dhiraj Thakur(Invincible) on 2011-06-23
> **BkkBonanza said:**
> I'm sure you googled but in case you didn't think of that - this useful link pops right up - stackoverflow often has really useful stuff, worth bookmarking.

[http://stackoverflow.com/questions/963305/python-library-framework-for-writing-p2p-applications](http://stackoverflow.com/questions/963305/python-library-framework-for-writing-p2p-applications)

I think if I were doing this I'd probably just write my own code as the basic idea isn't too hard. Open a listening socket and for each incoming connection spawn a thread to handle any commands received. What you actually do depends on your protocol you design.

Then your main loop might handle local stuff and spawn connections to other peers. Part of your protocol would result in a table of peers built from the incoming commands, eg. HELLO CMD comes and says "Hey I'm a peer" causes a new entry in peer table. You would want some kind of auth test of course so not just anyone can chat. You might look at the POP protocol as an example as it relates to sending messages, though I think even simpler can be done.
the problem is how to make the same computer both server and client at the same time...:(


and i dont want these heavy frameworks just to write a simple chat program....aren't thre any tutorials or buks that deal with Python p2p networking...i googled a lot nd cudn't find anything relevant....:(

---

### Post by Dhiraj Thakur(Invincible) on 2011-06-23
> **NovaAesa said:**
> If the chat is between only 2 computers, you could just take the easy way out, open a set of sockets and simply send the text straight through them.

Actually the peers can be more than two but for simplicity if it works for 10 peers atleast...i m gud

---

