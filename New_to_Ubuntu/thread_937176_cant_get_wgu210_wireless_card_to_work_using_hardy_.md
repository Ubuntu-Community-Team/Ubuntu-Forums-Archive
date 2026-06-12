---
title: "cant get wgu210 wireless card to work using hardy heron"
date: 2008-10-03
forum: New to Ubuntu
---

### Post by ACObuntu on 2008-10-03
Ok so I've been trying to get this wgu210 wireless card to work with my sony vaio pcg-fx210 for several days now.  I got the driver loaded using ndiswrapper and the card seems to recognize my router with the graphical utility because it gives me a signal strength.  The problem is that i cant connect to the internet and/or ping even the router.  I read something about the wireless radio button being off and that kind of seems like something to consider but i dont know how to even approch that. dmesg does recognize the device as wlan0 so i think all should be well, but it isn't.  If anyone knows what i should try or could offer any suggestions that would be greatly appreciated.  


thanks for any help you can provide.


i fear im wasting too much time on this but i feel like im getting very close to getting it to work.

---

### Post by phidia on 2008-10-03
If you open a terminal and enter > lshw -C network what is the output?
And while you have the terminal open also > ndiswrapper -l

Usually there is a physical switch somewhere that controls powering the card on and off-sometimes it's function keys though and that could be harder to get working.

One other thought: is the network you are trying to connect to open-that is do you need to enter a password to connect to it?

---

### Post by ACObuntu on 2008-10-03
the output of lshw -C network is
 *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:e0:b8:6c:8d:7a
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+wgu210 driverversion=1.52+Gateway,09/20/2003, 0.8.0.0 multicast=yes wireless=IEEE 802.11g
ndiswrapper -l 
driver is present and it states that the device is present as well.
there are no switches on the device itself. I am using wep with a 64bit network key but i have also tried with an open network. what do you mean by function keys? I did read somewhere about how a wireless radio is off by default to save battery life or something like that but i cant find anymore information about that.

thanks for helping does this output give any clues?

---

### Post by ACObuntu on 2008-10-03
So i did eventually get it to work without the wep.  dont know how but its working.  now i have to figure out why it wont work with the wep.

---

