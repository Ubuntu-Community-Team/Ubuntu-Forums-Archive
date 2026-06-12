---
title: "Working Wifi on Toshiba A215-S5837"
date: 2008-07-16
forum: New to Ubuntu
---

### Post by pgte3 on 2008-07-16
This may be helpful to someone. I was able to get the wireless card working on my Toshiba A215-S5837 running ubuntu 8.04.1 by doing the following:

Within Gnome desktop:
System-->Hardware Drivers--> uncheck (unenable) HAL 
 
From a terminal window:
wget [http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz](http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz)

tar xfz madwifi-ng-r2756+ar5007.tar.gz

sudo apt-get install build-essential

cd madwifi-ng-r2756+ar5007

sudo make

sudo make install

sudo modprobe ath_pci

sudo reboot

FYI

Here is a portion of my lshw output (note the product).

           *-network
                description: Wireless interface
                product: AR242x 802.11abg Wireless PCI Express Adapter
                vendor: Atheros Communications Inc.
                physical id: 0
                bus info: pci@0000:14:00.0
                logical name: wifi0
                version: 01
                serial: 00:1f:3a:8e:fa:8e
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list logical ethernet     physical wire

---

### Post by MatthewPlanchard on 2008-07-16
Cool, thanks for posting. :)

---

### Post by pgte3 on 2008-07-18
Beware that this manual install of a wifi driver is vulnerable to breaking if certain updates are made to your Ubuntu install. For example I believe that some kernel updates will break your wifi, and you made need to reinstall your driver again. Keep a good log of changes to your system.

---

### Post by markab9569 on 2008-07-25
when I do this I get the error "could not find build-essential" any suggestions

---

### Post by DagMan on 2008-07-26
sudo apt-get install build-essential

---

### Post by markab9569 on 2008-07-26
I can not get the linux machine to connect to the internet, can you tell me a url where I can get this program on my windows machine and "sneakernet" it over to the linux machine

---

### Post by pgte3 on 2008-08-04
Can you use a standard Ethernet cable connection?

---

