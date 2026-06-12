---
title: "linux kernel programming"
date: 2007-01-18
forum: Programming Talk
---

### Post by Silentvoice on 2007-01-18
I've just recently gotten into doing some linux kernel programming, and now for practice I'd like to mess around with some basic devices. Does anybody here know some good cheap and simple devices I might be able to get to kind of mess around with?

---

### Post by Hendrixski on 2007-01-18
There are a lot of devices that already run embedded Linux.  If you find one that hasn't had a Linux kernel installed on it, then it's a huge contribution to add another device to the list.  It's not just a game you know, it gets the attention of major companies and then they think "why the hell am I paying for an operating system on my product?"  Linux proliferates and the world becomes a better place.

---

### Post by cylon359 on 2007-01-18
You could try to control a stepper motor through a parallel port.... not really too useful generically, but you'd at least learn something.

---

### Post by std on 2007-01-19
Alternatively, if you're just starting out, you could try to write a driver for whatever device you are familiar with, even if it's already in the kernel. Your code will always be chunky when you're learning, so it's best if you can have a reference at hand if you get stuck (i.e. if you have someone else's code to look over when you need it).

Controlling a stepping motor is a good project though. My first attempt at this was with a simple LCD controller (displaying some custom message on a small LCD), which was also quite convenient since some other hacks like these were already around. You can just as well try to make a binary clock wired by parallel port (or serial port or whatever else -- this was my second atempt). Or, run a quick search through the projects they give to students at universities, they're usually public -- although you may find them a bit too... academic. I'm not sure about how often is Linux used there though -- as far as I've seen, Minix is prefered.

---

### Post by amo-ej1 on 2007-01-19
the annoying thing with a stepper motor or and lcd (in my eyes) is that it's overkill to controle those from kernel space since they are simply connected to your parallel or serial port ... so perhaps it's indeed better to play around with regular hardware you already have in your pc (and preferebly some hardware with the best documentation).

---

### Post by std on 2007-01-19
> **amo-ej1 said:**
> the annoying thing with a stepper motor or and lcd (in my eyes) is that it's overkill to controle those from kernel space since they are simply connected to your parallel or serial port

Very true as well. I suggested these having in mind the fact that the amount of things to remember/learn outside the kernel programming part is quite tiny.

---

### Post by winch on 2007-01-19
What about inventing your own filesystem and writing a driver for it? Using a loopback filesystem it would be contained within a file on disk. Might be easier to debug than a device driver, hardware often behaves like a black box if you don't talk to it correctly.

---

### Post by lank23 on 2007-03-19
Check this persons work out.

[http://communico.polito.it/gueli/step/](http://communico.polito.it/gueli/step/)

lank23

---

