---
title: "sinfo"
date: 2011-11-26
forum: New to Ubuntu
---

### Post by seattle vic on 2011-11-26
I just saw an article in the linux journal about sinfo, a utility to monitor performance of other machines, but I cannot get it to work.  It's in the repositories and I installed it, but when I simply type in > sinfo

/ 0 nodes, 0 CPUs   total CPU utilization:  -nan% ( 0.000 GHz / 0.000 GHz )

Trying to get info on another machine running sinfo:
> sinfo -h other_machine:60002

receive error: Host not found (authoritative).

Anybody have experience with this utility?

---

### Post by d4m1r on 2011-11-26
> **seattle vic said:**
> I just saw an article in the linux journal about sinfo, a utility to monitor performance of other machines, but I cannot get it to work.  It's in the repositories and I installed it, but when I simply type in > sinfo

/ 0 nodes, 0 CPUs   total CPU utilization:  -nan% ( 0.000 GHz / 0.000 GHz )

Trying to get info on another machine running sinfo:
> sinfo -h other_machine:60002

receive error: Host not found (authoritative).

Anybody have experience with this utility?


Is it on a local network or are you entering an IP? It seems to be a DNS issue, where it cannot connect to the machine. Try using the specific IP instead of the hostname.

---

### Post by seattle vic on 2011-11-26
I've tried both names and ip address, with and without ports (both 60001 and 60001, both opened up on the target machine.

But more basically, when you just type in

> sinfo

it should give you the status of your machine, just as:

> sinfo -h localhost
or
> sinfo -h 127.0.0.1

In any event I only get one line with no information.  The character in the first column is a rotating / so the program is running, but that's it.

---

