---
title: "Asterix in traceroute"
date: 2009-11-13
forum: Programming Talk
---

### Post by bonzi on 2009-11-13
Question regarding traceroute

```

11  reannz-1-is-jmb-776.sttlwa.pacificwave.net (207.231.241.18)  285.714 ms  285.755 ms  285.514 ms
12  210.7.47.21 (210.7.47.21)  428.770 ms  428.804 ms  428.914 ms
13  * * *
14  210.7.32.10 (210.7.32.10)  290.101 ms  290.216 ms  290.129 ms
15  fg.ac.nz (130.216.1.22)  290.329 ms  290.365 ms  290.522 ms


```I was tracerouting to 130.216.1.22
Does this mean that after 12th node it was timed out 3 times in node 13 and took an alternate path 14 (210.7.32.10) to the destination?? And is there anyway to know who 13 was??

---

### Post by lensman3 on 2009-11-13
From the traceroute man page:

"If the  probe  answers  come  from different gateways, the address of each responding system will be printed.  If there is no  response  within  a 5.0 seconds (default), an "*" is printed for that probe."

Some routers don't have a DNS-able IP address or the traceroute reply is dropped.

Take a look at the tracepath program, it will tell you if the path is symmetrical or asymmetrical. The to path is different from the return path.

---

