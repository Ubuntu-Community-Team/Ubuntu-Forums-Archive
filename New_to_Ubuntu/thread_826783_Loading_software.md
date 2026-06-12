---
title: "Loading software"
date: 2008-06-12
forum: New to Ubuntu
---

### Post by BadgerRay on 2008-06-12
Having a laptop with Windows 98 I decided to load Ubuntu. Having done so I now cannot load third party software 

message - "set-up .exe cannot be opened" no application suitable for automatic installation is available for handling this kind of file.

I need to load the software for my wireless card to connect to the internet

Any help please

Ray

---

### Post by Cypher on 2008-06-12
.EXE file are Windows executables that will not run in Linux. Post the specifics about your wireless card and others will guide you..

---

### Post by BadgerRay on 2008-06-12
Thanks for that. I have the disc for my Trendnet TEW-421PC Wireless PC Card IEEE 802.11g / 2.4GHz 54Mbps 

ps I am a very newbie to programming

---

### Post by Cypher on 2008-06-12
A couple of links to help you along, check out the first link first:
[http://ubuntuforums.org/showthread.php?t=201673](http://ubuntuforums.org/showthread.php?t=201673)
[http://acx100.sourceforge.net/](http://acx100.sourceforge.net/)

---

### Post by ukripper on 2008-06-12
> **BadgerRay said:**
> Having a laptop with Windows 98 I decided to load Ubuntu. Having done so I now cannot load third party software 

message - "set-up .exe cannot be opened" no application suitable for automatic installation is available for handling this kind of file.

I need to load the software for my wireless card to connect to the internet

Any help please

Ray

If you can go in terminal window and type following command and post output of it here:
```
lshw -C network
```

from here we can find out whether your wireless is configured or not.

---

