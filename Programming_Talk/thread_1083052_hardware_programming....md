---
title: "hardware programming..."
date: 2009-02-28
forum: Programming Talk
---

### Post by hockey97 on 2009-02-28
Hi, I am trying to look for source code or websites that can teach me the concepts behind encoding and decoding.

I do know c++ and c and python.  I never made a full blown out software.

I am curious to learn how logic chips are program to encode and decode stuff.

For example... like blue-ray and dvd encode and decode I am guessing those dvd players and blue-ray players would have a chip set to decode those formats.

you would only use a encode when you burning to make the dvd or blue-ray record something.

---

### Post by PythonPower on 2009-02-28
[OSDev]("http://www.osdev.org/") is your friend.

The guys there know hardware programming on a variety of devices and will likely point you in the right direction.

---

### Post by CptPicard on 2009-02-28
And, um, coding theory and hardware programming are two different subjects. Although of course you can do en/decoders in hardware, just like you can do other things in hardware...

---

### Post by Gordon Bennett on 2009-02-28
I suggest you start by learning combinatorial and sequential logic - use simulation programs to test ideas - there's plenty of apps out there like Klogic, Ksimus and so on.

Once confident you understand basic concepts (e.g. ripple addition, multiplication), you can then go a level higher and learn the gate-logic equivalent of C - VHDL or Verilog.

Note that most logic is programmed by dealing with mini state-machines (at this stage most high-level programmers will either be foaming at the mouth or unconscious).
You can then take a peek at the stuff in [OpenCores]("http://www.opencores.org/") to give you an outlook on more complex designs.

For implementing your own logic into chips, you can go for a simple FPGA (Field Programmable Gate Array) dev kit.    This will allow you to burn and re-burn your design netlist until it's right :P  You will also need a bit of electronics knowledge to wire it up.
There's also PLA's/CPLD's - Programmable Logic Arrays/Devices - which are usually used for simpler operations, but are cheaper to start practicing on.

Now, once you have that mastered, you can implement your dvd codec in gates :popcorn:

---

### Post by PythonPower on 2009-02-28
I would consider questioning whether you really need your own chips. Existing technology is sound as far as I have seen (did quite a bit of OS development a while ago).

---

### Post by mmix on 2009-02-28
opencores, seconded.
[http://www.opencores.org/projects.cgi/web/nova/overview](http://www.opencores.org/projects.cgi/web/nova/overview)

But, it doesn't mean hardware encoder/decoder always fastest.
[http://en.wikipedia.org/wiki/CoreAVC](http://en.wikipedia.org/wiki/CoreAVC)

---

### Post by CptPicard on 2009-03-01
> **Gordon Bennett said:**
> 
Note that most logic is programmed by dealing with mini state-machines (at this stage most high-level programmers will either be foaming at the mouth or unconscious).

Why would they be? State machines are perfectly valid, and even rather simple abstractions that have lots of interesting theoretical properties... a lot of low-level programmers are foaming at the mouth when they need to implement a state machine as a functional-programming monad... ;)

---

### Post by Gordon Bennett on 2009-03-01
> **CptPicard said:**
> Why would they be? State machines are perfectly valid, and even rather simple abstractions that have lots of interesting theoretical properties... a lot of low-level programmers are foaming at the mouth when they need to implement a state machine as a functional-programming monad... ;)

Most low-level programmers are concerned about getting the job done with an efficient implementation - over-egging it to satisfy linguistic ego just doesn't factor in their lives :P

---

