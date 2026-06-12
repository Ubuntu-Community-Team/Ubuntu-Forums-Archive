---
title: "how to set wire’s ip in 802.x"
date: 2011-10-01
forum: New to Ubuntu
---

### Post by Cynric on 2011-10-01
Hello&#65281;
I don't have a big experience with ubuntu,and I need little help.
My laptop is connected on my wire router,i want to change my static ip,
$sudo gedit /etc/network/interfaces auto lo
iface lo inet dhcp
auto et0
iface eth0 inet static
address 192.168.64.1
netmask 255.255.255.0
geteway 192.168.64.1
$sudo /etc/init.d/networking restart
$sudo gedit /etc/resolv.conf
nameserver 8.8.8.8
It doesn't work!
Help!:(
Tanks for help&#65281;

---

### Post by acrazyplayer on 2011-10-01
You have messed up the numbers. try finding a guide out there to help you set it up better. The guides numbers and yours will not be the same except for maybe the netmask.

in my case it looks like this. 

address 192.168.0.10
netmask 255.255.255.255
gateway 192.168.0.1

dns servers 4.2.2.3,8.8.8.8

 just do this by right clicking on the internet icon, then going to "edit connections" and from there I double click "atuo eth0"  go to the tab "ipv4 settings" 

for the "method" I choose "manual" and then you fill in all the boxes except search domains unless of course you know what you want there. good luck

---

### Post by haqking on 2011-10-01
> **Cynric said:**
> Hello&#65281;
I don't have a big experience with ubuntu,and I need little help.
My laptop is connected on my wire router,i want to change my static ip,
$sudo gedit /etc/network/interfaces auto lo
iface lo inet dhcp
auto et0
iface eth0 inet static
address 192.168.64.1
netmask 255.255.255.0
geteway 192.168.64.1
$sudo /etc/init.d/networking restart
$sudo gedit /etc/resolv.conf
nameserver 8.8.8.8
It doesn't work!
Help!:(
Tanks for help&#65281;

first of all when using a graphical app such as gedit you should use **gksudo** and not **sudo**

Then you have your LAN IP the same as your gateway address which is gateway and not geteway by the way.

Make sure your gateway is your routers LAN IP and your LAN IP is one valid for your LAN.

and if you have trouble use the GUI network manager to edit your connection

---

### Post by Cynric on 2011-10-01
Thanks,I think I find the point.

---

### Post by oldfred on 2011-10-01
I think you just have a typo:

geteway should be gateway.

---

