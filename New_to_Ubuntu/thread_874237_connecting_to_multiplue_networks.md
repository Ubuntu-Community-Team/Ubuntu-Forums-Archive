---
title: "connecting to multiplue networks"
date: 2008-07-29
forum: New to Ubuntu
---

### Post by trigsenior on 2008-07-29
hello there ,

I want to build a leeching box to leech of 4 networks with all different internet providers. You might want to know why i have 4 different wifi connections , well its because my tech savvy dad thought that like a mobile phone you needed a new provider for each person , my dad , me , my brother , sister and mother. He said he did it was because he thought that routers picked internet up from satellites  like phones :) 

So now we have 3 unused internet connections , so i decided to build a leeching box but is there a way to connect to all 3 networks at the same time and perhaps share the load in 3 ? i looked around on the internet and found a windows vista programm called virtual wifi. There anything linux programms which can do the same ? 

many thanks looking forward to you reply :popcorn:

---

### Post by halitech on 2008-07-29
I've never done this but I would think that if a machine has 3 network cards (wired would probably be best) and had a connection to each network it could in theory act as a server and bridge the connection down to a single system. I know one person that did it with 2 connections in windows XP but I don't talk to him so not sure how he did it

---

### Post by redmk2 on 2008-07-29
If you are looking to "load share" then you would be using the routing protocol BGP.  This is how large businesses on the telco's manage multiple connections to the internet.  Way beyond basic routing of a DSL, WiFi setup.  If you are looking into "bonding" the 4 interfaces together, I believe they must have that capability built in.  Server NIC's from 3Com had it.

If you are looking to "multi home" the box, then look into setting Ubuntu up as a router.

---

### Post by trigsenior on 2008-07-30
thanks ,for your reply they were very helpful , but i feel im a bit over my head here. I have had no experience with setting up servers or networking
However found this [http://brainstorm.ubuntu.com/idea/526/](http://brainstorm.ubuntu.com/idea/526/)  looks hopeful can't wait  for NetworkManager 0.7 =)

---

### Post by lisati on 2008-07-30
My question would be are you looking to connect to multiple ISPs at the same time? Unless you're prepared to fork out for multiple phone lines (or something similar) it could be difficult.....

---

### Post by trigsenior on 2008-07-30
> My question would be are you looking to connect to multiple ISPs at the same time? Unless you're prepared to fork out for multiple phone lines (or something similar) it could be difficult.....

You are right it all goes though one line so i would not get increased speed but the monthly download would not be so high as it shared out evenly between three providers.

---

