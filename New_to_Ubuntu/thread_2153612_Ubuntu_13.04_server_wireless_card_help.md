---
title: "Ubuntu 13.04 server wireless card help"
date: 2013-06-11
forum: New to Ubuntu
---

### Post by Werid41 on 2013-06-11
I have sucessfully installed the ubuntu 13.04 server and the 12.04 LTS precise desktop in dualboot. The laptop does have a wireless card already in, and ubuntu precise the wireless works. But in the server, the wireless card isn't found and I can only connect through ethernet cable
when I go to view the hardware there isn't even a wlan0
I've tried unblocking through rfkill but it wasn't soft blocked, the wireless isn't even there
lshw -c network doesn't display my wireless, it doesn't display anything in fact-- when in sudo 
any help would be very appreciated :)

---

### Post by zero2xiii on 2013-06-12
Hay,

Please see my thread here:
[http://ubuntuforums.org/showthread.php?t=2140012&p=12623446#post12623446](http://ubuntuforums.org/showthread.php?t=2140012&p=12623446#post12623446)
and supply us with more information.

It would be helpful including the ouputs from both systems (the one where the card IS working, and then the one where it is NOT working).

From there we can start figuring out why  it is not working, possibly a driver issue, so also include "lsmod".

Cheers

---

