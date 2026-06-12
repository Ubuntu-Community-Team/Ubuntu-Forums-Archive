---
title: "ethernet card problem"
date: 2008-06-18
forum: New to Ubuntu
---

### Post by coolnik6 on 2008-06-18
hi folks
 Internet is not working on my desktop with  8.04 LTS  but when i i used the same router with an laptop it worked
soo i guess problem is with ethernet card of my desktop
soo which ethernet card r supported by ubuntu??

---

### Post by sharks on 2008-06-18
Type in terminal :

Sudo pppoeconf 

and configure it.

---

### Post by MasterSander on 2008-06-18
Most ethernet cards are supported by ubuntu hardy, can you post the details of your card?

---

### Post by coolnik6 on 2008-06-18
Realtek RTL8139 Family PCI Fast Ethernet NIC

Driver version 5.398.613.2003

n this is for shark
i wud rather advice u to configure ur router in pppoe mode
then u dont even need the sudo pppoeconf

---

### Post by Pjotr123 on 2008-06-18
It could be this:
[http://ubuntutip.googlepages.com/nointernetconnection](http://ubuntutip.googlepages.com/nointernetconnection)
(number 2 )

---

### Post by MasterSander on 2008-06-18
[http://ubuntuforums.org/showthread.php?t=15786](http://ubuntuforums.org/showthread.php?t=15786)

This guy has the same problem.

---

### Post by MasterSander on 2008-06-18
[http://ubuntuforums.org/archive/index.php/t-407443.html](http://ubuntuforums.org/archive/index.php/t-407443.html)

They suggest using ndiswrapper here. What it basically does is run windows drivers on Linux.

---

