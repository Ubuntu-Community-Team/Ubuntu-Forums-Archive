---
title: "After I installed wifi network can`t configure my ethernet"
date: 2008-10-27
forum: New to Ubuntu
---

### Post by allarmguy on 2008-10-27
Hi!two days ago I installed my wireless network card,it work fine but now I can`t configure my Ethernet card.When I try to configure,I get only configure wlan0.What do I do wrong?

---

### Post by livestockPimp on 2008-10-27
can you post the output from "lspci", "lsmod" and "ifconfig -a"

---

### Post by allarmguy on 2008-10-27
I CAN`T... because that computer can`t go in internet

---

### Post by allarmguy on 2008-10-27
Is there a way to cancel my current configuration and return at the old one?

---

### Post by livestockPimp on 2008-10-27
not really,
firstly wlan0 is a wireless device and not your ethernet device. ethernet devices are normally "eth0", "eth1", ect. Most likely it is not configured. if you have dhcp on the router you connect to most likely "dhclient eth0" will get you back on the net. if you type "ifconfig -a" it will tell you all the network adapters you have (even those not configured or up). does "ethX" (insert number where X is) even appear when you input "ifconfig -a"?

---

### Post by allarmguy on 2008-10-27
NO!!!I get only wlan0 and l0 or lo,nothing eth

---

### Post by livestockPimp on 2008-10-27
ok, if the eth device does not show up when you use "ifconfig -a" then you need to load the module, the module you need to load depends on the network card. you can use "lspci" to list your internal devices and from here you should see a line that has all the info on your ethernet adapter, ie; intel pro 10/100. you will then need to load the module for your device. ie; "modprobe e1000"

I cannot tell you the module that you need to load since I dont know the ethernet adapter you have, if you can lspci and type the line of information about the ethernet adapter I can tell you how to get it working again.

---

