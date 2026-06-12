---
title: "wireless -card how to install?"
date: 2008-05-02
forum: New to Ubuntu
---

### Post by hazman on 2008-05-02
hi all,
just installed ubuntu 7.10 and dont know how to get my belkin wireless g card to work.i am a total novice only been installed 2 days, reinstalled x2 cos i messed setting up please help

---

### Post by master5o1 on 2008-05-02
Why 7.10 when 8.04 has just been released?

---

### Post by Michael.Godawski on 2008-05-02
I would always install the newest version of Ubuntu so 8.04.

Have a look here if your wlan card is supported in the first place:
[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBelkin?highlight=(belkin](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBelkin?highlight=(belkin))

To check what your wlan card is run these commands in terminal:

```
lspci

sudo lshw -C network
```

---

### Post by hazman on 2008-05-02
i installed 7.10 cos i was messing with the idea of swapping to linux awhile ago and downloaded it.since then cd writer broke on main computer.

lspci
ethernet controller:Belkin unknown device 701f [20]

lshw -C network
network unclaimed
descrition:ethernet controller
product:belkin
vendor:belkin
physical id:0
bus info: pci@0000:05:00.0
version:20
width:32 bits
clock:33MHz
capabilities;cap list
configuration:latency=0maxltency=64mingt32

---

### Post by zvacet on 2008-05-02
Check one of [these.]("https://wiki.ubuntu.com/?action=fullsearch&context=180&value=wifi&titlesearch=Titles")

---

### Post by hazman on 2008-05-02
hi,
followed the instruction on link but to no avail says hardware present:no

---

### Post by hazman on 2008-05-02
given up on linux going back to windows at least that works

---

