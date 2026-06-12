---
title: "kill pcap_open after a set amount of time"
date: 2007-07-23
forum: Programming Talk
---

### Post by B-Con on 2007-07-23
([Continued, sort of, from here.](http://ubuntuforums.org/showthread.php?t=497906))

I'm trying to use the pcap library to sniff packets on a machine, and I've run into a small problem.

The function pcap_loop() is used to listen for a specified number of packets. However, it has no timeout and will listen indefinitely for that number of packets. I want to impose a restriction on the amount of time that pcap_loop() will wait to receive a packet, because in the situation I'm in I don't know *if* I'll receive a packet, but I do know after how long I can assume that I'll never receive one.

The pcap_dispatch() offers a timeout function, but it's dependent on the system it's running and apparently Feisty doesn't satisfy it. Regardless, it's unreliable and not something I want to depend on should I move it to other computers.

My question isn't pcap-specific, though. I'd like to know if there's a way to execute an infinitely-looping function and forcibly kill it at a certain time. Maybe, would it be possible to start the function in a separate thread, maybe, and then kill the thread, or something like that?

Any suggestions would be appreciated.

---

