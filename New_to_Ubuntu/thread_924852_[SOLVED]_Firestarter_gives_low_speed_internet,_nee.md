---
title: "[SOLVED] Firestarter gives low speed internet, need help pls"
date: 2008-09-20
forum: New to Ubuntu
---

### Post by bred on 2008-09-20
Hi guys,
I have installed firestarter on Hardy,
something went wrong and I have a very slow dnload speed after changing a rule in firestarter, is there a way to switch back from my "dumb"rules to by default rules?
Before firestarter i had a excellent speed, now I'm blocked, have no idea what to do...
There is a way to Reset firestarter or iptabes?

Thank you in advance.

---

### Post by Ocxic on 2008-09-20
try using firewall builder, little more intense but offers much better firewall planning

---

### Post by zvacet on 2008-09-20
You can use [ufw]("http://www.ubuntugeek.com/ufw-uncomplicated-firewall-for-ubuntu-hardy.html") instead of firestarter.You can install GUI from [here.]("http://linux.softpedia.com/downloadTag/ufw+GUI")

---

### Post by bred on 2008-09-20
firewall builder and ufw did not help me...thx anyway

there is a way to reset/restore all rules of iptable by default - as a new one?

---

### Post by gandaran on 2008-09-20
the latest Gufw firewall [http://gufw.tuxfamily.org/](http://gufw.tuxfamily.org/) will help you, its better and easier to setup than firestarter, remove firestarter first then install Gufw, in Gufw there is a tab where you choose the bittorrent or download program you are using, [http://img67.imageshack.us/my.php?image=example2pq6.png](http://img67.imageshack.us/my.php?image=example2pq6.png)  just choose the application and it will open up the ports.
if you still prefer firestarter then find out which ports you application needs, then open them in the rules tab

> there is a way to reset/restore all rules of iptable by default - as a new one?
I think once you install firestarter it closes up all ports, if you remove firestarter they will still remain closed. probably there is a command to restore the defaults settings, but I don't know it.

---

### Post by bred on 2008-09-23
finally Gufw solved my problem
thx guys

---

