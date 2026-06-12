---
title: "Need a good Networking library - c++"
date: 2007-07-16
forum: Programming Talk
---

### Post by Pocket Aces on 2007-07-16
Well I think I've made a horrible mistake and I need help.  Working alone under a harsh deadline I threw a lot of good coding practices to the wind and just started hacking anything together to get a functional demo in time for a deadline.

My application is distributed in three parts communicating over the network.  Right now I'm using sockets and the libsocketc++ library from sourceforge.  Unfortunately, as progress has been made it is becoming clear to me this was a terrible mistake.  At the initial design it was really only thought of as one part pushing data over the network to the other.  Now we need to add a fair amount of data travelling both directions and accessible by a number of discrete portions of the code.

Is there any library for C++ on linux that can make the network more transparent?  Ideally I would love to be able to treat the network communication as no big deal and just pass data around as if it was all on the same machine.

---

### Post by slavik on 2007-07-16
> **Pocket Aces said:**
> Well I think I've made a horrible mistake and I need help.  Working alone under a harsh deadline I threw a lot of good coding practices to the wind and just started hacking anything together to get a functional demo in time for a deadline.

My application is distributed in three parts communicating over the network.  Right now I'm using sockets and the libsocketc++ library from sourceforge.  Unfortunately, as progress has been made it is becoming clear to me this was a terrible mistake.  At the initial design it was really only thought of as one part pushing data over the network to the other.  Now we need to add a fair amount of data travelling both directions and accessible by a number of discrete portions of the code.

Is there any library for C++ on linux that can make the network more transparent?  Ideally I would love to be able to treat the network communication as no big deal and just pass data around as if it was all on the same machine.

aren't you already using read() and write()? (maybe encapsulate that?)

---

