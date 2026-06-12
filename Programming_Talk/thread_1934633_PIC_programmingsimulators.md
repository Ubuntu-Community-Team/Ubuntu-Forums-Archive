---
title: "PIC programming/simulators"
date: 2012-03-02
forum: Programming Talk
---

### Post by darylt on 2012-03-02
Hi,

Not sure if I'm in the right forum (apologises if not).

I'm been thinking of getting into PIC micro controller programming for some small projects, and was wondering if anyone could point me in the right direction of software for my Ubuntu 11.10 system?

---

### Post by alexfish on 2012-03-03
there is gpsim

but will only run in terminal mode , so need earlier versions of Ubuntu

[https://bugs.launchpad.net/ubuntu/+source/gpsim/+bug/626287](https://bugs.launchpad.net/ubuntu/+source/gpsim/+bug/626287)

if only for 16C84 try nitpic . 16F84 simulpic

there is a listing for 
 A Java based emulator that you can use online.
    Includes hardware simulation by Java applets.
    Version 1.7.9 is open source, and available for download.

[miSim DE]("http://www.feertech.com/misim")

[http://www.feertech.com/misim/homepage.html]("http://www.feertech.com/misim")

Try it on Line
[http://www.feertech.com/misim/homepage.html](http://www.feertech.com/misim/homepage.html)

other route is to install wine , to use windows programs ,

---

### Post by darylt on 2012-03-03
:(

i was getting somewhere but glib wont install.

Stupid question: Why wont it work on the newer versions of Ubuntu?

---

### Post by alexfish on 2012-03-04
> **darylt said:**
> :(

i was getting somewhere but glib wont install.

Stupid question: Why wont it work on the newer versions of Ubuntu?

GTK versions are different RE: gtkextra

the link is above RE: launch pad,

if need GUI the try using the Java Link , if no Java on the system install it

---

