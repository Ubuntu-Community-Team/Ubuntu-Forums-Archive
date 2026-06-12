---
title: "[SOLVED] Deleted Network Manager"
date: 2008-11-24
forum: New to Ubuntu
---

### Post by rich70734 on 2008-11-24
I have accidentally deleted Network Manager from my Ubuntu system. I have no idea how to get it back. I can't get my computer to connect to the internet now. Can anybody give me a hand?

---

### Post by AllanPoe on 2008-11-24
Reinstall it through Aplications>add/remove

---

### Post by lswb on 2008-11-24
Method 1) Start synaptic, click on Settings/repositories follow instructions to install from live CD. After installation click "reload" in synaptic and install upgrades if applicable.

Method 2, if you have a wired ethernet connection, interface name is eth0, using dhcp, which is the most common scenario, open a terminal and type these commands:

sudo ifconfig eth0 up
sudo dhclient eth0

If you have wireless it's a little more complicated, but if you have an unsecured network (no WEP or WPA) and your wireless interface name is say eth1, and your wifi network essid (name) is "mynetwork" it wo
uld be something like this:

sudo ifconfig eth1 down
sudo iwconfig eth1 mode managed essid "mynetwork"
sudo ifconfig eth1 up
sudo dhclient eth1

---

### Post by rich70734 on 2008-11-24
Thanks! Now I can finally connect to the internet from the Ubuntu half of my computer again.

---

### Post by Gotlieb on 2010-11-23
You are a Star !! Thaynx !! It Solved my Problem Too !!

---

