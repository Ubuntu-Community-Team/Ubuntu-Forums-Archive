---
title: "Shell Script with Sudo, directions anyone?"
date: 2008-08-03
forum: New to Ubuntu
---

### Post by NickZA on 2008-08-03
Hello Fellow Ubuntites

Having just happily gotten NAT/ICS running on my two ubuntu systems (I am saying goodbye to MS all at once), I now need to get NAT/ICS to be persistent between reboots.

I've identified the shell commands I need to execute on startup to get everything running as it should:

```
sudo ifconfig eth0 192.168.0.1
sudo iptables -A FORWARD -i eth0 -o eth1 -s 192.168.0.0/24 -m state --state NEW -j ACCEPT
sudo iptables -A FORWARD -m state --state ESTABLISHED,RELATED -j ACCEPT
sudo iptables -A POSTROUTING -t nat -j MASQUERADE 
```

...All others settings I need have already been saved to various .conf files in /etc.

AFAIK, I must somehow edit sudoers (can I use gedit for this?) to give some user (can I use myself, i.e. the user I usually log in with?) permission to run these specific 2 commands, ifconfig and iptables. Do I understand this right?? Can someone tell me what on earth I have to do/type, exactly?

With your help, soon I will reclaim my sanity from Gates! :mad:


-Nick

---

### Post by GreenN00b on 2008-08-03
The ip address can be set by editing the file /etc/network/interfaces

As for iptables settings iptables has an option to save and restore settings, you should save the settings to a file and then have iptables load them at startup.

---

### Post by NickZA on 2008-08-04
Hey -- you rock.

Got me on the right track, I managed to find the last few remaining pieces of the puzzle and I now have a persistent NAT/ICS setup. I've written this all into a fairly straightforward & comprehensive tutorial for myself to use next time (whenever that may be), but would happily post it somewhere useful for others if someone could direct me...

Last order of business, Samba.

Thanks again pal.

-Nick

---

### Post by bodhi.zazen on 2008-08-04
In general, any script you will run as root should be owned by root and writable only by root.

You then run the script as root (sudo script).

Also rather then calling an application "iptables" use the full path, or set a variable to save on typing.

```
#!/bin/bash
IPTABLES='/sbin/iptables'

$IPTABLES -A FORWARD -i eth0 -o eth1 -s 192.168.0.0/24 -m state --state NEW -j ACCEPT

$IPTABLES -A FORWARD -m state --state ESTABLISHED,RELATED -j ACCEPT

$IPTABLES -A POSTROUTING -t nat -j MASQUERADE
```

These are small points, but are important for security :)

---

### Post by NickZA on 2008-08-05
excellent,

thanks for those little nuggets, bodhi.zazen... useful to absorb stuff like that right now while I'm on this path. :)

-Nick

---

### Post by hyper_ch on 2008-08-05
what I did on my boss's notebook is writing two small shell script that just replace /etc/network/interfaces with the according settings and restart networking.

I then made launchers to launch each script and he'll have to enter the password.

I needed that because in one office he requires static IP and in the other one dynamic IP.

Maybe that's enough for yuo also.

---

### Post by bodhi.zazen on 2008-08-05
Off topic:

hyper_ch :

You might want to look at wicd, it allows profiles for various networks.

I have had some success with it :

[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

> Profiles for each wireless network and wired network

---

### Post by hyper_ch on 2008-08-05
bodhi.zazen

I made just two interfaces text files and the script just replaces the existing one with the desired one and restart networking. Very simple and works just fine ;)

---

### Post by bodhi.zazen on 2008-08-05
Sweet, the old adage "If it's not broken, don't fix it" applies.

Might help in the future or help others, I don't know ???

---

