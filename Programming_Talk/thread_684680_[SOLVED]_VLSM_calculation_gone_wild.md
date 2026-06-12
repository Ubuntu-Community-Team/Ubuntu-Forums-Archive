---
title: "[SOLVED] VLSM calculation gone wild"
date: 2008-02-01
forum: Programming Talk
---

### Post by jingo811 on 2008-02-01
I posted for some tips and help regarding VLSM calculation before in "Servers & Security" but I didn't get any feedback.  So I thought of asking it in "Programmers Talk" even though there's no programming involved.  I figured programmers are good at the theoretical level and also good with math.

So I try it here with a sexy heading :)


[SIZE="4"]Problem:[/SIZE]
I'm trying to implement my VLSM knowledge in real life by calculating by hand and subnetting networks between routers.  I get my knowledge from 3-4 different sources none of them explains or shows anything completely so I mix all the info which causes my math to result in **"ip address overlaps"**.

Lets start from this point.  Can somebody explain why netA used the 4th octet 64 and not netA: 204.15.5.0 /28?
```

netA# 204.15.5.64 /28
netA# nnnn nnnn . nnnn nnnn . nnnn nnnn . ssss hhhh
netA# nnnn nnnn . nnnn nnnn . nnnn nnnn . s1ss hhhh
```

Isn't this the most logical way to describe the beginning /28 subnets?
```
netA# 204.15.5.0 /28
netA# nnnn nnnn . nnnn nnnn . nnnn nnnn . ssss hhhh
netA# nnnn nnnn . nnnn nnnn . nnnn nnnn . sss(o) hhhh
```


[http://www.cisco.com/warp/public/701/3.html#vlsmexample](http://www.cisco.com/warp/public/701/3.html#vlsmexample)

```
netB: 204.15.5.0/27  host address range 1 to 30
netE: 204.15.5.32/27 host address range 33 to 62
netA: 204.15.5.64/28 host address range 65 to 78
netD: 204.15.5.80/28 host address range 81 to 94
netC: 204.15.5.96/30 host address range 97 to 98
```

---

### Post by PaulFr on 2008-02-03
If I understand your question correctly, the answer is because the two /27 networks in the VLSM example (netB and netE) already have taken those addresses.

The first available IP address after those networks are accounted for is 204.15.5.64, and based on the number of hosts needed in netA, netA is given 204.15.5.64/28.

If you used (as you suggested) 204.15.5.0/28, then that would translate to IP addresses 204.15.5.1 thru 204.15.5.14. But netB's 204.15.5.0/27 would translate to IP addresses 204.15.5.1 thru 204.15.5.30. That is an overlap for the IP addresses.

---

### Post by jingo811 on 2008-02-04
Tnx for the feedback it's the first in 2-3 weeks.  This subject is the most complicated I have tried to explain and verbalize into a question.  I even had trouble presenting my problems with all my notes and pictures to point at in real life.

But I think I see now where my logic has flawed and how to properly mix my sources of knowledge that didn't come exclusively from Cisco.
This picture made me see again.

[IMG]http://i27.tinypic.com/2it3g5k.png[/IMG]

---

