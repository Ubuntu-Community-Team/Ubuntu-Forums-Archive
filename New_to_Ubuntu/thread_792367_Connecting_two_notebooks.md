---
title: "Connecting two notebooks"
date: 2008-05-12
forum: New to Ubuntu
---

### Post by O-pos on 2008-05-12
Hi, how can I connect a laptop with Ubuntu Hardy to another laptop with Windows? I want to copy large data from that computer. Is there special cable? 

Thanks in advance

---

### Post by overdrank on 2008-05-12
> **O-pos said:**
> Hi, how can I connect a laptop with Ubuntu Hardy to another laptop with Windows? I want to copy large data from that computer. Is there special cable? 

Thanks in advance

HI and I believe that would be a crossover cable.

---

### Post by O-pos on 2008-05-12
Do you know any link or guide how they do it on Ubuntu?

---

### Post by overdrank on 2008-05-12
> **O-pos said:**
> Do you know any link or guide how they do it on Ubuntu?

HI and you may find some here
[http://www.uboontu.com/results.htm?cx=002072379199720138921%3A9m-bgfzutzq&cof=FORID%3A10&q=cossover+cable+in+ubuntu&sa.x=0&sa.y=0&sa=Search#1141](http://www.uboontu.com/results.htm?cx=002072379199720138921%3A9m-bgfzutzq&cof=FORID%3A10&q=cossover+cable+in+ubuntu&sa.x=0&sa.y=0&sa=Search#1141)

---

### Post by mrsteveman1 on 2008-05-12
Depends on what you want to do. The only connections fast enough to do this are fast ethernet which tops out at around 4MB/s, USB which tops out around 25MB/s, firewire at around 35MB/s, and gigabit ethernet which can hit 65MB/s.

There are some "transfer cables" for USB but i believe they are windows only, however you can still just copy stuff to a USB drive and move the drive, its reasonably fast.

Everything else is networking, so you can just use samba or ssh to move the files. Do you know how to network them together?

---

### Post by inportb on 2008-05-12
> **mrsteveman1 said:**
> fast ethernet ... tops out at around 4MB/s

Eh? I have gotten Ethernet rates in excess of 10 MB/s, and it was not on a gigabit network. Try using a crossover cable. You gotta manually assign IP addresses for both machines.

---

### Post by mrsteveman1 on 2008-05-12
4MB is probably a bit low, but it depends on the protocol. Yea throwing layer 2 frames back and forth you can hit pretty high speeds but most protocols are more complicated and higher up, and have some serious overhead. Samba can sometimes hit 6MB/s but I've never seen anything higher.

How the IP was assigned shouldn't matter, DHCP sticks the IP in the kernel just like you would if you set it manually, in either case the speed is literally identical.

---

