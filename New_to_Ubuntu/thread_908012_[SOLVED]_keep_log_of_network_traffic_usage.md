---
title: "[SOLVED] keep log of network traffic usage"
date: 2008-09-02
forum: New to Ubuntu
---

### Post by Circus-Killer on 2008-09-02
i am currently using a 3g connection connected to the internet. on this package, i only have 1gb before i have to start paying per mb. so naturally, i want to keep track so that i can stop using it when i hit 1gb.

i was wondering if anyone knows how i can keep track of network usage over an extended period of time. ultimately, the best solution for me would be to just keep track of the network flow on ppp0 interface, and then after each session, save the usage to a file for later use. unfortunately, i have no idea how to go about doing this.

any help would be much appreciated.

---

### Post by lucho64 on 2008-09-02
> **Circus-Killer said:**
> i am currently using a 3g connection connected to the internet. on this package, i only have 1gb before i have to start paying per mb. so naturally, i want to keep track so that i can stop using it when i hit 1gb.

i was wondering if anyone knows how i can keep track of network usage over an extended period of time. ultimately, the best solution for me would be to just keep track of the network flow on ppp0 interface, and then after each session, save the usage to a file for later use. unfortunately, i have no idea how to go about doing this.

any help would be much appreciated.

I just tried this on my connection and it seems to do what you need. I mean, it just prints the number of bytes, but you could make it sound an alarm or bring down the connection, or whatever. Sorry about using gawk, I'm just more used to it than, say perl, or whatever else.

```
tcpdump -i eth1 -e -n -q|gawk '{if (match($0,"length [0-9]+")){l=l+1*substr($0,RSTART+7,RLENGTH-7);print l;}}'
```

So i guess you could start this in /etc/rc.local

---

### Post by Circus-Killer on 2008-09-03
well, i just found darkstat and think i'm just going to use that.
seems to keep track of the usage pretty well.

---

