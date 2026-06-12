---
title: "wifi button no work in ub8.04 on compaq presario a900 laptop who had vista installed"
date: 2008-10-25
forum: New to Ubuntu
---

### Post by damien666 on 2008-10-25
tried iwconfig    ...lo        no wireless extensions.

eth0      no wireless extensions.

tried installing from apt get and synaptic  ndiswrapper-common and ndiswrapper-utils-1.9

dont know what to do ... been 3 days three days I try please if u can help...

Damien

---

### Post by shifty_powers on 2008-10-25
what is the output of ```
lspci
```?

---

### Post by damien666 on 2008-10-25
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
02:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)


here it is

---

### Post by shifty_powers on 2008-10-25
have you tried [http://madwifi.org/](http://madwifi.org/) ?

the madwifi drivers are designed for atheros chipsets.

```
01:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
```


might be just what you need...

[http://madwifi.org/wiki/UserDocs/FirstTimeHowTo](http://madwifi.org/wiki/UserDocs/FirstTimeHowTo)

---

### Post by damien666 on 2008-10-25
all right I will try and get back to you thanks a million....I got it but im not sure what to do with it... I will try some more but some help would be greatly appreciated...
sorry for my neewbyism  hehe
D

---

### Post by damien666 on 2008-10-25
I did  apt-get install build-essential in terminal and I got 
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

then I tried sudo nano apt-get install build-essential but I got this funky terminal GNU nano 2.0.7  .....I tried that cuz I read it somewhere to go in root menu but got no where ... sorry

---

### Post by shifty_powers on 2008-10-26
close

```
sudo apt-get install build-essential
```

is what you want...

---

### Post by damien666 on 2008-10-30
still no work... nothing works... the ethernet dosent even work now, it sees the connection, connects but cant acces the the internet ...  the built in camera and mic dosent work ...the wifi button dosent work... this suks...does anybody know what to do ... a compaq a900 upgrade or something..... I even tried the new ubuntu 10 still NOTHING WORKS...   I reinstalled ubuntu 8.04 and the wired network still dosent work but it works fine with windows xp on an other laptop  WTF  ...

---

### Post by larschristian on 2008-11-16
Hi

Works for me with the new ath5k driver in Ubuntu 8.10
You might have to install the backports to get the ath5k driver to work. [Check here for more info]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/289014").

Only thing not working is that the wifi light isn't changing color. It's always orange and never shifts to blue. 

However I'm having a problem with file system corruption on my A900. Probably a faulty hard drive with bad blocks, but I haven't been able to confirm that yet.

Think this laptop is the first for me which everything works without ANY proprietary drivers. :-). A first for laptops at least. 



.lars

---

