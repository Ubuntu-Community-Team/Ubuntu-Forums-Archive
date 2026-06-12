---
title: "Can't connect to Internet"
date: 2008-06-29
forum: New to Ubuntu
---

### Post by belikralj on 2008-06-29
I've got Ubuntu 7.10 on my acer laptop. It recognises all of my network cards fine but I can't figure out how to get it to work with my d-link router. The router is set up to give DHCP but Ubuntu still can't connect to the net. Please help!

---

### Post by Matthewslf on 2008-06-29
First, check for the little things like if you have an on/off button for the wireless card. After that, I personally use a shell script to connect which is:

int='eth1'
ip='192.168.1.111'
gate='192.168.1.1'
essid='networkname'
killall NetworkManager
ifconfig $int down
killall dhclient
dhclient -r $int
iwconfig $int essid $essid
iwconfig $int mode Managed
ifconfig $int $ip netmask 255.255.255.0 up
route add default gw $gate

Substitute your network's name for networkname and your interface (iwconfig in terminal to find out) for eth1. I like my ip to be .111, but use whatever you want. You need to run it as root. If you want to undo the changes, type "sudo NetworkManager". The script shuts down dhcp and the automatic network configuaration and does it 'manually' instead.

---

### Post by belikralj on 2008-06-30
it didn't work. I don't know exactly why. Also even when I try just connecting via ethernet cable to the router I still can't conect to the internet.

---

