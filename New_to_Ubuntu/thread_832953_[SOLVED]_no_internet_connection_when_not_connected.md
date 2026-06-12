---
title: "[SOLVED] no internet connection when not connected at startup"
date: 2008-06-18
forum: New to Ubuntu
---

### Post by nesmoT on 2008-06-18
Hi everyone!

When I start up my computer without having the modem connected, I won't have any internet connection. 

However, when there is a connection while I start up the machine I will have internet. 

So each time I forget about connecting the computer to the modem before I startup my computer, I have to connect the computer to the modem and restart again.

It does not help to try dhclient when my computer has no internet connection.

I use kubuntu 8.04.

---

### Post by aquavitae on 2008-06-18
Try the terminal command
```
sudo /etc/init.d/networking restart
```
after plugging the modem in.

---

### Post by nesmoT on 2008-06-18
Thanks! That solved the problem. I tried it out right away and 

> sudo /etc/init.d/networking restart

does the trick.

:)

---

