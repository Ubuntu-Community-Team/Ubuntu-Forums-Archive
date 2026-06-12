---
title: "Help with network wireless on new laptop install"
date: 2008-06-06
forum: New to Ubuntu
---

### Post by happytechie on 2008-06-06
OK, total newbie here so be gentle with me.

I'm trying to get ubuntu running on my laptop

I't a pcworld £200 special by esystems, I have no idea what wireless hardware in installed in it and no real way of finding out without taking the machine apart and reading component IDs. It worked fine under windows.

lshw -C network gives me:

description: wireless network
physical id: 1
logical name: wlan100
serial: 00:15:af:0a:6e:5f
capabilities: ethernet physical wireless
configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

iwconfig gives me the right settings for my wireless network, ESSID is correct and there is more data there, but too much to type in if it's useless.

I'm connecting to the net now using another (windows) laptop.

I have tried reading anbd following some guides but they all seem to tell me to type a command and then know what to do on the basis of the output, I'm not at that level with ubuntu yet I'm afraid and any help would be appreciated

The wireless card under windows is turned on and off via a dedicated button on the laptop.  This button does not seem to function under ubuntu (the light doesn't come on) but it may well be driver specific I guess?

---

### Post by happytechie on 2008-06-06
lspci does not identify my wireless device just the wired one (Ethernet controller Realtek Semiconductor co ltd RTL8111/8168B PCI Express Gigabit ethernet controller (rev 01)

---

### Post by happytechie on 2008-06-06
and then I enabled roaming in the network manager thing and entered my password for my network this is now being posted from my new ubuntu installation:D

---

### Post by Xerp on 2008-06-06
w00t :) Huzzah for DHCP!

---

