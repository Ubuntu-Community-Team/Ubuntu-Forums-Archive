---
title: "Binary AND (&amp;) on null characters"
date: 2006-03-01
forum: Programming Talk
---

### Post by blacklantern on 2006-03-01
For one of my projects, I'm sending packets from a server to a client using UDP protocol. I've also been given a troll program that all packets have to pass through. I can set the troll to drop, garble, and delay a percentage of those packets. 

Right now, I'm only setting the troll to garble a percentage of my packets. To combat this, I'm implementing Cyclic Redundancy Check in my code. However, the reference CRC code I've been given uses a bitwise AND & for all characters (btw, I'm working in C). The messages I'm sending are in the form of structures, which I clear out with Null characters before every use. It's an all purpose message, one I'm using for ACKS, new transfer indicators, etc. So, there are some times where I don't even bother to change some members of the struct from nulls, because I know that the receiver won't be reading those fields. However, with the binary AND (&) that I'll be using in my CRC code, I'm wondering - how does that operator respond to NULL characters?

---

### Post by thumper on 2006-03-01
NULL is just zero (almost certainly on all platforms that you'll be using).

anything & zero == zero.

---

### Post by jerome bettis on 2006-03-01
also UDP will drop random packets, garble some of them, and doesn't guarantee the order to be correct.

i was doing a project that sent disk requests over the network, and i wanted the speed of UDP so i tried it.  for a few days i couldn't figure out why my incoming data was _completely_ screwed up ... lots of wasted time changing stuff with my code that was right.  then i read that this is normal behavior for UDP, so i changed the socket to use TCP and all was well, albeit slower.  lol, do your homework before you use stuff like that i guess.

edit
[http://www.linktionary.com/u/udp.html]("http://www.linktionary.com/u/udp.html")
scroll down there's a nice table

---

### Post by blacklantern on 2006-03-01
Well, in this project we're required to use UDP, since we're trying to build our own reliable link. And even though UDP potentially could drop UDP packets, the university network is pretty reliable, so I won't usually see any of the problems caused by UDP protocol. That's where this troll program comes in - it'll allow me to create some problems myself, for my program to try and overcome with ACKS, CRC, Sliding Window, etc. 

In any case, as long as I know that nulls won't mess with the & operator, you guys have all been a great help.

---

