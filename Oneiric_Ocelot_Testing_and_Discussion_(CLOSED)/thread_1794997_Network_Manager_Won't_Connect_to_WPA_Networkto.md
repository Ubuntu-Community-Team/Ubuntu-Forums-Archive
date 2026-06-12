---
title: "Network Manager Won't Connect to WPA Networkto"
date: 2011-07-01
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by roadkillbunny on 2011-07-01
After I upgraded to Oneiric a few weeks ago, the network manager won't connect to my home network which is using WPA encryption. It asks for my password, which I type in correctly, and then just tried to connect until it fails.

I don't think it is a problem with my wireless driver, since I have no trouble connecting by stopping the network-manager service and using wpa_supplicant from command line.

---

### Post by bennachie on 2011-07-02
I've had no problem with either Ubuntu or (better) Kubuntu Oneiric in connecting to WPA-protected networks (tested on a desktop, laptop and netbook, all pretty much mainstream devices). There may well be some problem specific to your system set-up. Perhaps, if you could provide a few more details about that set-up, somebody here may have the answer.

---

### Post by lucazade on 2011-07-02
check if there is a default keyring for storing wifi password, open a terminal and paste:
seahorse

if there are errors paste here.. check also if gnome-keyring is correctly installed.

---

