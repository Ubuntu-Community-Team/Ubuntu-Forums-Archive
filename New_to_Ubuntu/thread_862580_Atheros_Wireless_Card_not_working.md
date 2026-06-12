---
title: "Atheros Wireless Card not working"
date: 2008-07-17
forum: New to Ubuntu
---

### Post by roviltalon on 2008-07-17
Hey, sorry about my total n00bness again!!
I have just installed Ubuntu(HH) on my HP Pavillion DV9702EA laptop, im pretty sure I am using an atheros wireless card?? It isnt connecting to or displaying any networks whatsoever even though ubuntu has said the restricted atheros driver was enabled. Any help would be greatly greatly appreciated! I dont really know anything about running any programs/using sudo/accessing directories through the terminal! =(

---

### Post by seagullplayer77 on 2008-07-17
I've got the feeling that my laptop isn't all that different than yours (HP Pavillion dv9000 series), and I had a problem not all that much unlike yours when I was trying to get my wireless Internet up and running. That was a while ago, so I'm not sure I'll be able to remember everything I did, but I'll try to help anyway. First things first, the proprietary driver will NOT work at all, so you're gonna have to do something different. Try following this tutorial:

[http://ubuntuforums.org/showthread.php?t=792158](http://ubuntuforums.org/showthread.php?t=792158)

I'm not sure if you're running the 32- or the 64-bit version of Ubuntu, but you can get tutorials for both versions from that link. Good luck!

---

### Post by ibuclaw on 2008-07-17
what is the output of this command? (ran in a terminal)
```
sudo lshw -short | grep network
```

I'm on a DV2750 (Intel Wireless 4965 on my side).

Atheros Drivers should work straight off with the ath_pci modules...

Check your "Hardware Drivers" manager: ( System -> Administration -> Hardware Drivers ) and check that everything is enabled.

Regards
Iain

---

### Post by seagullplayer77 on 2008-07-17
Just another quick word of caution: I'm not entirely sure that following that tutorial will fix all your problems right away. I had to do (and still have to do) a few other extra things before I can even hope to connect to a wireless network. So if that tutorial isn't the magic cure-all, don't be disappointed. We can still probably make it work!

---

