---
title: "Network Application"
date: 2009-08-29
forum: Programming Talk
---

### Post by nebu on 2009-08-29
I am trying to build a network application like IPMessenger(in windows) in java for my ubuntu box....


id reall like to know how this actually works....

im kind of confused as to how do i find everyone using this app are online on the network....

do i have to loop through all the ips in the network and check if the application is running on a specific port??

---

### Post by supirman on 2009-08-30
To see what the application is doing, you can capture the network traffic with a sniffer such as wireshark.

Also, you would send a broadcast message instead of individually trying to query each IP on a network.  Each machine running the app would periodically broadcast its presence and the other machines would hear the broadcast and add the IP to their list of known chat machines.

---

