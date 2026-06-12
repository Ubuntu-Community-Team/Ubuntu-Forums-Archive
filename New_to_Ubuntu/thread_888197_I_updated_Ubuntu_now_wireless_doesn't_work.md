---
title: "I updated Ubuntu now wireless doesn't work"
date: 2008-08-12
forum: New to Ubuntu
---

### Post by deleyd on 2008-08-12
I updated Ubuntu. Said there were over 200 updates. So I applied the updates. And now I can't connect to the internet. But I can still connect to other computers on my local network.

Not only that, I can't connect to the internet when I boot into Vista. This is a dual boot laptop with Vista & Ubuntu.

I originally got the Ubuntu wireless working by blindly following some commands someone had posted, and much to my surprise it actually worked, even though I had no idea what I was doing. Do I have to do that over again? (I don't recall where those instructions were.)


ASIDE:
Does Ubuntu make changes that affect Vista? When I first installed Ubuntu the screen didn't seem as bright. I searched the forums and found some way to make the screen brighter, at least bright enough.

But now the screen also seems a bit dimmer when I boot into Vista. Just wondering if there's any hardware interaction between Ubuntu and Vista. I originally believed the two OS were completely separate, with Vista on one partition and Ubuntu on another, and no matter how bad I screwed up Ubuntu, it wouldn't make Vista any better (or worse).

---

### Post by pytheas22 on 2008-08-12
If you post the output of these commands, I can try to figure out how to make the wireless work again:
```

lshw -C Network
lspci -nn
lsusb
iwlist scan
```

> But now the screen also seems a bit dimmer when I boot into Vista. Just wondering if there's any hardware interaction between Ubuntu and Vista. I originally believed the two OS were completely separate, with Vista on one partition and Ubuntu on another, and no matter how bad I screwed up Ubuntu, it wouldn't make Vista any better (or worse).

There should not be any interaction.  In rare cases Windows is known to do stuff like power-down certain devices (especially ethernet cards) and cause problems for Ubuntu, but I've never heard of Ubuntu affecting Vista.  Maybe your monitor was set dimmer by an external switch, though.  Are there buttons on the monitor to set screen brightness?

I have no idea how upgrading Ubuntu could affect the wireless in Vista.  You might try pulling the power cord from your computer for a while (this solves issues where a device got put into sleep mode or something weird), but if that doesn't help, it's probably just a coincidence.

---

### Post by deleyd on 2008-08-12
Thank you for the commands. I now think it's not Ubuntu but rather a home network problem, as I discovered another computer can't connect, even though some other computers can connect, such as the one I'm using now.

This home network has been a PITB. Sometimes it works perfectly, all six computers connect to the internet and they all see each other. Other times things just don't work. 

It's all Linksys gear. Is Linksys a bad company to get home networking hardware from?

Anyway it's apparently not an Ubuntu problem.

---

### Post by mrsteveman1 on 2008-08-12
On the software side, nothing in an ubuntu update should affect vista selectively, it would more likely corrupt the vista partition than do specific things like you mentioned.

The screen brightness though is a hardware thing. Most laptops have specific buttons for screen brightness, and it can be controlled by software as well. As of recently, both kubuntu and ubuntu can control screen brightness automatically and i think they dim it by default in some situations. There are certainly function keys to fix it though, and Vista also has a software panel for brightness, i think its in the mobility settings.

As for the network, if you can access local stuff, the system is working fine. The only difference between local stuff and internet stuff, is a default route, and a dns entry.

You can check for a default route by just typing route in the terminal. If you see an entry like this:

```
ubuntu@ubuntu:/$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 eth1
default         192.168.1.1     0.0.0.0         UG    100    0        0 eth1

```

Then the routing is fine. If not you can add one like this if you know the ip of your router:

```
sudo route add default gw 192.168.1.1
```

Then the next thing is the dns resolver, which is listed in /etc/resolv.conf like this:

```
ubuntu@ubuntu:/$ cat /etc/resolv.conf
nameserver xxx.xxx.xxx.xxx
nameserver xxx.xxx.xxx.xxx

```

You can also edit that file to add them if you know what they are, but your router should have all this information and should have given it to your system when it grabbed an IP address, assuming DHCP is still being used (and it should be unless its been changed).

---

