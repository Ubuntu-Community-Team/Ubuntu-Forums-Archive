---
title: "[SOLVED] how do i portforward deluge and transmission"
date: 2008-08-16
forum: New to Ubuntu
---

### Post by marine63 on 2008-08-16
i looked at my transmission port and the program said the port was closed... seeing that ubuntu's firewall is disabled by default what could be causing the port to be closed even though i port forwarded it in the router?

---

### Post by Vivaldi Gloria on 2008-08-16
> **marine63 said:**
> i looked at my transmission port and the program said the port was closed... seeing that ubuntu's firewall is disabled by default what could be causing the port to be closed even though i port forwarded it in the router?

Are you sure you port forwarded right in your router?

Here is a howto port forward I wrote to someone else. Read it and see if you have omitted something.


**1)** Enter the router settings. Every decent router has a setting or table where you can fix the adresses of particular computer (ethernet card). Find that setting which fixes your computer's adress. If there is no such setting then this guide is no good for you.  It can be something of the sorts "Always use the ip 192.168.XX.XX for the computer with the mac adres XX:XX:...". I choose a number like 192.168.1.35. Restart router.

**2)** In a terminal give the command ifconfig. Here is the top lines of its output from my box:

```
vivaldi@narval:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:07:c4:d2:17:ba  
          inet addr:192.168.1.35 ...
...
...
```

Here eth0 is the my main ethernet card. The ip 192.168.1.35 is the ip fixed by the router for that card. So at this step we verify that you indeed get the ip the router reserved for your computer.

**3)** Now since your computer's ip is fixed to 192.168.1.35 you can forward the ports you want to 192.168.1.35. Use your port forward settings (or NAT) of your router to do this. For example when you start transmission you can learn the port number it uses from its settings menu. Mine uses TCP 51413. For transmission I the use the following 

start & end ports: TCP 51413, ip:192.168.1.35

in my router.


**4)** Some routers also have a seperate firewall settings in which you may also need to enable ports.

---

### Post by marine63 on 2008-08-16
thx :D

---

