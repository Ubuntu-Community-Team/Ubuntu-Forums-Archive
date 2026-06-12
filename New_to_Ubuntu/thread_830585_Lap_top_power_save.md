---
title: "Lap top power save"
date: 2008-06-16
forum: New to Ubuntu
---

### Post by nynoah on 2008-06-16
A friend of mine is running Linux mint (a derivative of Ubuntu).  She wants to know if there are any programs out there that will help her extend the life of her battery.  Some kind of program that will shut off all things that are not needed.  She needs to have it running in class for notes and the net and that is all.

Any words of advice?

---

### Post by sdennie on 2008-06-16
There are many ways to save power with a Linux laptop.  Check [www.lesswatts.org](www.lesswatts.org) and also the powertop tool:

```

sudo apt-get install powertop
sudo powertop

```

You can also use laptop-mode or a simple script harness to automate the things at lesswatts or from powertop.  For the latter, see [http://ubuntuforums.org/showthread.php?p=4960691](http://ubuntuforums.org/showthread.php?p=4960691) for an example on how to set things up.

---

### Post by nynoah on 2008-06-16
Thanks Vor.  I will check those things out.

---

### Post by eldragon on 2008-06-16
in my experience, powertop is useless...but i might be using it wrong :(

there is a thread on undervolting core duos, might or might not work ono your friends, and its more complicated to setup, but it could double your friends battery life.

check it here: [http://ubuntuforums.org/showthread.php?t=786402](http://ubuntuforums.org/showthread.php?t=786402)

---

### Post by nynoah on 2008-06-16
Thanks I will check that one out too

---

### Post by sdennie on 2008-06-16
> **eldragon said:**
> in my experience, powertop is useless...but i might be using it wrong :(

there is a thread on undervolting core duos, might or might not work ono your friends, and its more complicated to setup, but it could double your friends battery life.

check it here: [http://ubuntuforums.org/showthread.php?t=786402](http://ubuntuforums.org/showthread.php?t=786402)

It would be impossible to double your battery power by undervolting unless you are using the machine in such a way that it never reaches the C3 sleep state (in which case, your battery life is going to be poor regardless).  In fact, I've not seen any evidence (though I've asked several times in that thread) that undervolting makes huge difference in power savings.

---

### Post by InfinityCircuit on 2008-06-16
Undervolting seems to be somewhat dangerous given the comments in that thread.  I'd try powertop first.

---

### Post by fiddledd on 2008-06-16
You might find this interesting:

[http://www.linuxmint.com/forum/viewtopic.php?f=58&t=12533&p=77696&hilit=fred+data+writeback#p77696](http://www.linuxmint.com/forum/viewtopic.php?f=58&t=12533&p=77696&hilit=fred+data+writeback#p77696)

It's not exactly about power saving, but I'm guessing less Disk activity = less power consumption. It also apparently speeds up your System, I'm not however vouching for it, as I've not tried it, yet.

---

### Post by eldragon on 2008-06-16
> **vor said:**
> It would be impossible to double your battery power by undervolting unless you are using the machine in such a way that it never reaches the C3 sleep state (in which case, your battery life is going to be poor regardless).  In fact, I've not seen any evidence (though I've asked several times in that thread) that undervolting makes huge difference in power savings.

id trust undervolting, considering that power consumtion in digital switching is proportional to the power supply voltage and switching frequency. 

i find there is something really wrong with linux regarding power consumption and noone is really caring about it.

all of this out of my own experience.

i bought this notebook which came with vista, battery life (3cell pack, whatever that means) lasted about 2:30 minutes (of realtime measured use). 

i could never get it past the 1hour of battery use under linux. first gutsy and then hardy.

tried compiz off. tried powertop, tried undervolting (which doesnt work on this notebook....see the aforementioned thread)

tickless or no tickless kernel, something is making this computer thirsty under linux, and i fail to see what it is.

btw, soy de buenos aires tambien.

---

### Post by sdennie on 2008-06-16
> **eldragon said:**
> id trust undervolting, considering that power consumtion in digital switching is proportional to the power supply voltage and switching frequency. 

i find there is something really wrong with linux regarding power consumption and noone is really caring about it.

all of this out of my own experience.

i bought this notebook which came with vista, battery life (3cell pack, whatever that means) lasted about 2:30 minutes (of realtime measured use). 

i could never get it past the 1hour of battery use under linux. first gutsy and then hardy.

tried compiz off. tried powertop, tried undervolting (which doesnt work on this notebook....see the aforementioned thread)

tickless or no tickless kernel, something is making this computer thirsty under linux, and i fail to see what it is.


I think people care about power savings (I'm a power savings fanatic in fact) but, there are currently no "Push This Button" kinds of solutions for linux so you end up having to use powertop, [www.lesswatts.org](www.lesswatts.org) and scripts to get the job done.  My guess is that a lot of the power savings done on Windows is done by the vendor specifically for that machine.  Linux doesn't have that luxury and so it's sort of a do it yourself job at the moment.

Having said that, I'd bet it wouldn't be too hard to get your laptop battery life as good or better than Windows.  You are welcome to PM me with your system specs and I'll be glad to help out (or post the system specs in a new thread in Hardware and Laptops section and I can help there too).

> 
btw, soy de buenos aires tambien.

Saludos.

---

