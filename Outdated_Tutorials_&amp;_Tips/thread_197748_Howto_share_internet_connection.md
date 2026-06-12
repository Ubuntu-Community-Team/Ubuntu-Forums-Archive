---
title: "Howto share internet connection"
date: 2006-06-16
forum: Outdated Tutorials &amp; Tips
---

### Post by schultzconsult on 2006-06-16
After reading and strugling with [http://www.ubuntuforums.org/showthread.php?t=91370]("http://www.ubuntuforums.org/showthread.php?t=91370") I desided to write a new howto for 6.06, so here we go.

You need 2 network cards, I used a ethernet network card and a wireless network card, but it will do with any kind of networking cards.

my setup is as follows:
wireless nic for internet connection called wlan0
ethernet nic for local network called eth0

wlan0 is set up with DHCP and have 
IP            :  192.168.1.3
netmask :  255.255.255.0
ns           : 192.168.1.254
gateway : 192.168.1.254

eth0 is set up with static and have
IP            : 192.168.2.1
netmask : 255.255.255.0
ns           : 192.168.2.1
gateway : none

assign adresses to your cards in you computer like mine above. But you need to make sure, that your internet connection side (in my case wlan0) does not have the same IP range as the local network side (in my case eth0).

We need to install firestarter with
```
sudo apt-get install firestarter
``` 
then we need to set up DNS proxy with:

```
sudo apt-get install pdnsd
``` 

edit /etc/pdnsd.conf:
```
nano /etc/pdnsd.conf
``` 
change the lines to match your DNS settings and your local network card configuration.

```
        server_ip="192.168.2.1";
``` should be the IP of your local network card (eth0)

```
/*
server {
        ip="192.168.1.254";
        timeout=30;
        interval=30;
        uptest=ping;
        ping_timeout=50;
        purge_cache=off;
}
*/

``` 
remove the /* and */ around the above block and change the ip="192.168.1.254" to the ip of your internet DNS server ip.

save and exit.

now we need to set up the computers on the local network.

Each computer needs settings like:

IP            : 192.168.2.n
netmask : 255.255.255.0
ns           : 192.168.2.1
gateway : 192.168.2.1

where n is a new number for each new computer, but not 1.

When you have done that, you should be able to ping 192.168.2.1 from every computer on the local network, but not to ping anything on the internet.
We now begin to set up the routing of the traffic from the local network to the internet side.

start firestarter and follow the guide, select your internet bound nic for internet side and local nic for local network side.
Start up the firewall if it is not allready running.
Now you should be able to ping any IP on the internet.

If you have any services, which is not let trough the firewall look in the events log in firestarter, find the blocked event from the given IP and right click on it and select "Allow connections from source"

You should be up and running now.

---

### Post by sloarch07 on 2007-02-24
Thanks for this great tutorial.  I got everything up and running on my first try.  I didn't find where to set my "ns" setting but it worked without it.

---

### Post by Frenzy-br on 2007-03-16
now how would i go about doing that with only one network card... 
i did it just fine when i used windows but now ...

---

### Post by Jastonite on 2007-10-23
Thanks a bunch!  I've been looking for a way to share my wireless internet connection from my Ubuntu laptop for quite some time now, and this is the first one to actually work for me!

---

### Post by disneyfriedhistory on 2007-10-28
How much more difficult is it to go in the reverse direction, that is, to have the wired eth0 be the WAN and a wireless card (for me, eth1)  acting as a wireless router for the LAN?

---

### Post by tednumber8 on 2009-01-12
Can this be done with et0 to internet and shared over wlan0?

---

