---
title: "Can't run custom app"
date: 2016-10-22
forum: New to Ubuntu
---

### Post by MadleSs on 2016-10-22
Hi guys, 
Just now I installed Anylogic 7 and I'm not able to run it. I have installed it into /usr/bin/anylogic/ folder and it only runs if I run it as root. I have created launcher entry using alacarte, but it's not possible to run it. Can you help me how can I run it as root from launcher? 

Thank you

---

### Post by deadflowr on 2016-10-22
What's the launcher command you made for it in alacarte?

---

### Post by MadleSs on 2016-10-22
```
/usr/bin/anylogic/anylogic
```

---

### Post by MadleSs on 2016-10-22
This happens if I run it from terminal ... Without root rights it won't run not telling why, with root privileges runs with warning...
[http://imgur.com/a/j3qUa](http://imgur.com/a/j3qUa)

---

### Post by monkeybrain20122 on 2016-10-22
Better ask anylogic.

---

### Post by yetimon_64 on 2016-10-22
> **MadleSs said:**
> This happens if I run it from terminal ... Without root rights it won't run not telling why, with root privileges runs with warning...
[http://imgur.com/a/j3qUa](http://imgur.com/a/j3qUa)

Note: anylogic is a graphical application ! 

I saw that same error "The owner of ~/.config/ibus/bus is not root" recently when testing "sudo" vs "sudo -H" on a graphical application here very recently. 

As anylogic is a graphical application I would suggest you use the "-H" switch with sudo when launching it from a terminal. Doing so here removed that error with my testing of recent for a thread. 

Better still (when running it from a launcher, like the alacarte one) is to use pkexec or to install gksu and use either gksu or gksudo for graphical applications (if anylogic needs to be run as root. I have no idea about that applications normal use at present, you will need to check for that detail yourself).

> Better ask anylogic.         +1. A much better idea is to go to the source of the application than a general linux forum. At least on 14.04 it is not in the standard ubuntu repositories.

---

