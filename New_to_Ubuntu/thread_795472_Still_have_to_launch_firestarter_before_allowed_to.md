---
title: "Still have to launch firestarter before allowed to do anything online"
date: 2008-05-15
forum: New to Ubuntu
---

### Post by UnWarierMage224 on 2008-05-15
Hi folks, 

So I followed the directions here: 
[http://ubuntuforums.org/showthread.php?t=542756](http://ubuntuforums.org/showthread.php?t=542756)

To my understanding, these directions will load your iptables config at boot, so that when you login to ubuntu the firewall rules will be in effect, yes? 

Now my problem is that I have iptables configured using firestarter but when I boot I do not have firestarter running... Without firestarter running I can't do anything (no internet, period... no IMAP, SMTP, NOTHING). 

EDIT: Rather, I have to launch and close firestarter once before I can do anything. It DOES NOT have to be running in the background. 

I'm not sure what to do. 

-'Mage

---

### Post by wolfen69 on 2008-05-15
is there a specific reason you use firestarter? your computer will be protected without it. removing it may solve your problem. just a thought.

---

### Post by UnWarierMage224 on 2008-05-15
I uninstalled firestarter... no internet connectivity whatsoever, still. 

I tried the following command also: 

```

sudo iptables --flush

```

That command does not erase my iptables for some reason.... so that PC is still in lockdown. No internet, period. 

What to do?

-'Mage

---

### Post by Journeyman on 2008-05-15
The problem there is that the defaults are to deny everything, you need to change it to allow:

iptables --policy OUTPUT ACCEPT

change OUTPUT to INPUT if you want to default allow all things coming in, this I don't suggest you should make custom rules for that.

---

### Post by bodhi.zazen on 2008-05-15
[http://www.ubuntugeek.com/ufw-uncomplicated-firewall-for-ubuntu-hardy.html](http://www.ubuntugeek.com/ufw-uncomplicated-firewall-for-ubuntu-hardy.html)
[https://help.ubuntu.com/8.04/serverguide/C/firewall.html](https://help.ubuntu.com/8.04/serverguide/C/firewall.html)

So ...

```
sudo apt-get remove --purge firestarter
sudo iptables -F
```Then ```
sudo /etc/init.d/networking restart
```Last ```
sudo ufw enable
```The other option is to start learning iptables or use an alternate gui.

I am sad to say, firestarter is not has helpful as in the past and it (firestarter) has issues. ufw makes it outdated. If it (firestarter) works, great, but firestarter breaks more and more often over time, in my opinion. Firestarter also fails with complex networking, wich is more and more common with virtualization and wireless.

ufw is easy to learn and configures iptables much easier and the defaults are superior to running without ufw or the defaults with firestarter.

if ufw is not working, we need to know more about your network.

---

### Post by UnWarierMage224 on 2008-05-15
Bodhi: I followed what you said, also installed gnome-lokkit.

So far, everything is right with the (linux) world on my PC.

-'Mage

---

