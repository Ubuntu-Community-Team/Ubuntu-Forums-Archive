---
title: "Can't connect to wifi"
date: 2016-12-03
forum: New to Ubuntu
---

### Post by jswerveholby on 2016-12-03
I just installed Ubuntu today (first time linux user) and I'm having issues connecting to wifi.  The wifi works on other devices, so the problem seems to be with my laptop.
I checked all the software settings, reset my bios, restarted in multiple different ways, made sure my hardware switch is on, and researched.  I still can't figure this out.

My wifi appears to be hardware blocked, but I can't figure out how to unblock it.  Ethernet works (which is how I'm on this forum) but wifi will not.

```


jswerveholby@jswerveholby-VPCEE31FX:~$ sudo rfkill list all
[sudo] password for jswerveholby: 
0: sony-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes


```

What should I do?

---

### Post by wildmanne39 on 2016-12-03
Hardblock means the card is turned off, and should be able to be turned on with the switch or by using the fn+ f5 key for example, once you get it turned on if you still have problems run the wireless script in my signature and post the results here.

---

