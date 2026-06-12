---
title: "[SOLVED] Does Ubuntu lock down all my ports?"
date: 2008-06-02
forum: New to Ubuntu
---

### Post by Bigtime_Scrub on 2008-06-02
I'm using Azureus and I never EVER get green smiles on my connection. I'm wondering if my ports are closed and if they are how to find my router's IP address in Ubuntu. I know how to do it in Windows but I'm clueless how to do it in linux.

---

### Post by HotShotDJ on 2008-06-02
> **Bigtime_Scrub said:**
> how to find my router's IP address in Ubuntu. I know how to do it in Windows but I'm clueless how to do it in linux.:confused:  Why would your router's IP address be effected by the Operating system?  I use my router's user manual to get my router's IP address.  You can get your computer's IP address by opening a terminal (Applications -> Accessories -> Terminal) and typing ifconfig and looking for the proper device (or you could add the device to the end of the command, for example "ifconfig eth0" or "ifconfig wlan0")

---

### Post by kesman on 2008-06-02
Usually the IP address can be found in the manual or from the bottom of your router.

In windows, azureus uses UPnP to automatically ask the router to open ports for torrents, this doesn't work in linux and isn't very safe either. You will have to manually open the ports.

---

### Post by Bigtime_Scrub on 2008-06-02
> **HotShotDJ said:**
> :confused:  Why would your router's IP address be effected by the Operating system?  I use my router's user manual to get my router's IP address.  You can get your computer's IP address by opening a terminal (Applications -> Accessories -> Terminal) and typing ifconfig and looking for the proper device (or you could add the device to the end of the command, for example "ifconfig eth0" or "ifconfig wlan0")

From the Azureus Help Page:



[http://www.azureuswiki.com/index.php/NAT_problem](http://www.azureuswiki.com/index.php/NAT_problem)
Port Forwarding on Linux, specifically Ubuntu

Firstly the earlier notes on port forwarding for your router apply as before. Computers running Ubuntu, by default, come with all the ports locked down and you need to open the ports in ubuntu by using the iptables command. Other flavours of linux behave similarly

The commands below can be entered in a root terminal session to open the ports (TCP and UDP)

iptables -I INPUT -p tcp --dport <your_port_number> -j ACCEPT
iptables -I INPUT -p udp --dport <your_port_number> -j ACCEPT

<your_port_number> is the port number you have used for port forwarding (Avoid 6881-6999, any from 49125-65535 is fine)

Once you've established the port is open you need to make the change persist through a reboot

---

### Post by iaculallad on 2008-06-02
To get your default gateway (IP address of your router):

Type this on your terminal:

```

netstat -rn
```

---

### Post by HotShotDJ on 2008-06-02
> **iaculallad said:**
> To get your default gateway (IP address of your router):

Type this on your terminal:

```

netstat -rn
```I never knew that!  Brilliant! ;)

---

### Post by Bigtime_Scrub on 2008-06-02
> **iaculallad said:**
> To get your default gateway (IP address of your router):

Type this on your terminal:

```

netstat -rn
```

Thank you that was exactly what I was looking for. It's a simple code too.

---

### Post by iaculallad on 2008-06-02
You're welcome. Go Ubuntu

---

### Post by Bigtime_Scrub on 2008-06-02
Here is a How To Guide for Azureus in Ubuntu.

If you use torrents and you never get the green smiles in Azureus, you have a Network Access Translation (NAT) problem. What it means is that you don't get good download speeds and it takes forever.

This is not good if your downloading Distros and what not like me. I wanted to get the Knoppix 5.1.1 DVD which is 4 gigs. A download like that can take days because of a NAT problem!

Here is a solution.

First you need to get your router IP address.

Open a terminal and type:
```
netstat -rn
```

You should get an output with a table and a bunch of numbers. Look at the column with "Gateway" and go to the bottom of that column. There should be an IP number there most likely starting with 192.XXX.X.XXX

Take that number and copy/paste it into the Firefox web browser and hit enter.

The page you are on is your router's "homepage." It is also your network.
Double click and get into your network configuration table. It is usually password protected. If it isn't password protected I suggest that you enable one. If you don't know the password it might be in your owners manual or if you lost it (like me) you will need to contact your IP provider (that is the company you pay for internet service).

You will see a feature within the configuration window that allows you to create a static IP address. You will need to do this so click on it. I don't know how much this screen can vary so I cant tell you exactly how to find it but what you are looking for is  a DHCP range. It could be under option, configuration or tools. 

It is a range of IP addresses (ex: 192.168.1.100 - 192.168.1.149) You will have to enter an IP address that is outside of this range. For the range above an IP of 192.168.1.200 will suffice. This will create a static IP so go ahead and save/exit out of there. YOu will lose your internet connect for a minute so don't freak out it will be back up shortly. 

Please restart both your computer and router. Unplug the router and hit the little reset button it has.

When you get back on the internet you will have a static internal and private IP address for Azureus (or really whatever your torrent down loader is). Log into your router configuration table again. (enter the IP address you got earlier and go to the same place as earlier.) You are going to do Port Forwarding through the router. The section you are looking for will probably be NAT, NATP, Custom Services, or Virtual Server. It can be named almost anything though but how you do it will be the same.

If you are very lucky there are step by step specific router guides found here:
[http://www.portforward.com/routers.htm](http://www.portforward.com/routers.htm)



Just find your router in that list and go. If it isnt on that list:

The Rule will need its own Name/Number
The Rule will also need a port to forward to. (if it ask for a range use the same number twice)
Use TCP and UDP as the protocol (if it doesn't ask for protocol than these are both there as default)
If you can only choose 1 protocol then you will need to have two rules for that port (make a new name/number and use the same port)
Assign forwarding to the static IP address you gave yourself earlier
click on save/apply.

Now open terminal (Applications ->Accessories-> Terminal)

```
iptables -I INPUT -p tcp --dport <your_port_number> -j ACCEPT
```
```
iptables -I INPUT -p udp --dport <your_port_number> -j ACCEPT 
```
<your_port_number> is the port number you you made in the configuration table you just did. (DO NOT USE 6881-6999)

After this you need to reboot. 

create a file /etc/init.d/iptables_azureus and add the lines below
        (sleep 220
         /sbin/iptables -I INPUT -p tcp --dport <your_port_number> -j ACCEPT
         /sbin/iptables -I INPUT -p udp --dport <your_port_number> -j ACCEPT ) &


In terminal:
```
chmod +x /etc/init.d/iptables_azureus
```
```
  update-rc.d iptables_azureus start 51 S .
```

That's it! have a happy and fast d/l.


If anyone feels like something should be added feel free to do so and constructive criticism is always welcome. I hope someone finds this useful. Many many references to the azureus help page but I feel like it needs to be here too because new users might not have any idea where to go to find help for this and the more places it is the easier it is to find.

---

