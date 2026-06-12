---
title: "Device Driver Problems (As I assume)"
date: 2013-02-14
forum: New to Ubuntu
---

### Post by loveguzzy on 2013-02-14
hey there....I am kinda new to ubuntu, I just installed Ubuntu 12.10 to my HP 630 laptop but having some problems like :
* connecting to the Internet
* bluetooth function not working
* touchpad features not working
* card reader 

An I presume that this a device driver problem which I have no idea what to do :(

I tried the 'lspci' and i got the wireless adapter model I suppose

"02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)"

"03:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5209 PCI Express Card Reader (rev01)"

Hoping for a reply asap.. Thankyou

---

### Post by auxilium on 2013-02-14
hi,

you may do this in terminal to check your hardware use

```
lshw
```to check if the driver for the hardware are installed use

```
lsmod
```to open terminal press the buttons at the same time

CTRL ALT t

---

### Post by auxilium on 2013-02-14
I did some research and you need the compatible backport driver..check this out

[http://askubuntu.com/questions/67437/how-do-i-install-a-driver-for-an-atheros-ar9285](http://askubuntu.com/questions/67437/how-do-i-install-a-driver-for-an-atheros-ar9285)

---

### Post by loveguzzy on 2013-02-14
> **auxilium said:**
> hi,

you may do this in terminal to check your hardware use

```
lshw
```to check if the driver for the hardware are installed use

```
lsmod
```to open terminal press the buttons at the same time

CTRL ALT t


When I tried lshw and browsed down, I came across this . Does it have something to do with the problem?

       *-network DISABLED
                description: Wireless interface
                product: AR9285 Wireless Network Adapter (PCI-Express)
                vendor: Atheros Communications Inc.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: wlan0
                version: 01
                serial: 74:de:2b:29:2f:88
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ath9k driverversion=3.5.0-17-generic firmware=N/A latency=0 link=no

---

### Post by loveguzzy on 2013-02-15
> **auxilium said:**
> I did some research and you need the compatible backport driver..check this out

[http://askubuntu.com/questions/67437/how-do-i-install-a-driver-for-an-atheros-ar9285](http://askubuntu.com/questions/67437/how-do-i-install-a-driver-for-an-atheros-ar9285)
This is my rfkill list, and i tried adding the blacklist acer_wmi but still the problem persists

root@loveguzzy:~# rfkill list
0: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
2: hp-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
3: hp-bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no

---

### Post by sandyd on 2013-02-15
Have you tried any of the Wifi Hardware switches at boot?

---

### Post by Nr90 on 2013-02-15
have you tried
sudo rfkill unblock all
?

---

### Post by loveguzzy on 2013-02-15
> **auxilium said:**
> I did some research and you need the compatible backport driver..check this out

[http://askubuntu.com/questions/67437/how-do-i-install-a-driver-for-an-atheros-ar9285](http://askubuntu.com/questions/67437/how-do-i-install-a-driver-for-an-atheros-ar9285)


I kinda browsed through it and installed the backports, and it works. Thank you Aux :) :popcorn:

---

### Post by loveguzzy on 2013-02-15
Thank you all for your support, I installed the backports through the ubuntu software center and also the touchpad features as well...now it works perfect.  bUbye ):P

---

### Post by Nr90 on 2013-02-15
Then you could/should mark this thread as solved :)

---

### Post by loveguzzy on 2013-02-15
> **Nr90 said:**
> Then you could/should mark this thread as solved :)

Like I said, Um a newbie..... :D:p):P

---

