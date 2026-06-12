---
title: "Can internet connect be activated on startup?"
date: 2006-09-05
forum: Outdated Tutorials &amp; Tips
---

### Post by dalani on 2006-09-05
can internet connect be activated on startup? I have to type in my root password to connect ot the net via a dialup connection. If someone elese wants to use my computer that means having to give them my root passward (no can do!) 

I set up a guest desktop user as default bootup user but cant configure it to connect to the internet iether at startup or during user session without the use of root passwrd. Its; mostly for my wife who wants to be able to use the internet without my having to intervene. Ideally I would a 'kiosk' mode of operation (turn on computer: browser and connection all done).

Any help would be appreciated.

---

### Post by dalani on 2006-09-11
Yes it can be activated on startup. Mark this solved- I guess those man pages are good for something after all). Now when my users boot, the internet connection is already up and running.

How? I configured etc/network/interfaces to activate my Wvdial (which handles pppd). The solution is simply to edit the etc/network/interfaces files to activate the network connection under 'auto' . The method of choice for me was Wvdial, others are ppp, static address, dhcp etc...good luck with the syntax.


----------------------------------------------
Weapons of mass destruction? the tons of toxic wastes dumped illegally worldwide.

---

