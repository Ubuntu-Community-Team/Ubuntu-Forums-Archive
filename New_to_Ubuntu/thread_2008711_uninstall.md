---
title: "uninstall"
date: 2012-06-23
forum: New to Ubuntu
---

### Post by leilton on 2012-06-23
Have Ubuntu 12.04 installed, also installed Xubuntu,(from synaptic manager), to see if liked it.

Decided that no reason to keep it, and went back to synaptic manager to remove itl, however, bit confused, what is  difference between remove and remove completely? don´t want to make any silly mistakes.

Also is this the correct way, i.e. ticking all the relevant boxes or is there a quicker way?

---

### Post by qyot27 on 2012-06-23
> **leilton said:**
> Have Ubuntu 12.04 installed, also installed Xubuntu,(from synaptic manager), to see if liked it.

Decided that no reason to keep it, and went back to synaptic manager to remove itl, however, bit confused, what is  difference between remove and remove completely? don´t want to make any silly mistakes.

Also is this the correct way, i.e. ticking all the relevant boxes or is there a quicker way?
'Remove completely' is the equivalent of apt-get's 'purge' command.  It removes both the programs themselves and any lingering configuration files.

This distinction may not matter much these days, though.  Some of the options seem to hint that 'remove' is being treated like 'remove completely' anyway.  I still purposely use purge/'Remove completely' when uninstalling things, though.

---

### Post by QIII on 2012-06-23
Don't just blindly unplug all things Xubuntu using Synaptic or you may find yourself staring at a blank screen and pulling your hair.  You'll probably end up with no DE at all.  

Have look at [this]("http://www.psychocats.net/ubuntu/pureubuntu") at psychocats.

Psychocats is a great resource and worth poking around.  If I'm not mistaken, a forum staff member by the handle aysiu maintains it.

What you are describing as your goal would be a bit hard one thing at a time -- there would be dependency issues.  It also assumes you would know exactly what you were looking for from the start.

---

