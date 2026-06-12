---
title: "ADSL PPPoE connection in 8.04 LTS KDE"
date: 2008-07-20
forum: New to Ubuntu
---

### Post by germantechie on 2008-07-20
I am new to linux.
i want to access interent through my ADSL modem.
went through many posts. did as they said by using pppoeconf
it displayed the success message ( .... loaded)

but the browser is not able to open up sites.
from network settings the manual ip is set to default 192.168.1.1
and gateway as 255.255.255.0

---

### Post by pfdevil on 2008-08-31
Hey, this is probaly to late now. 

But the solution to your problem is. The gateway can't be 255.255.255.0 <-- This is your subnet mask. I think that the 192.168.1.1 that is actually your default gateway. Thus you should choose your ip in the range 192.168.1.2 -> 192.168.1.255. You can see if the pppoe connection was esthablished by typing plog in the terminal. Also ifconfig then there should be a ppp0 connection.

Cheers

---

