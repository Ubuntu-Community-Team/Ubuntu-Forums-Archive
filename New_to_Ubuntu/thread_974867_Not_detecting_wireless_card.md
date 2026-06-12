---
title: "Not detecting wireless card"
date: 2008-11-07
forum: New to Ubuntu
---

### Post by igmlopes on 2008-11-07
Hey!

I just tested Ubuntu for the first time, running from the CD.
But I´m afraid of installing that for real coz it didnt detect my wireless card.

- Atheros Hardware Access Layer (HAL)
- Support for Atheros 802.11 Wireless Lan Cards

Anyone, helpppp!!!

---

### Post by Patrick793 on 2008-11-07
Well, plug in an ethernet cord, and install like usual.

You need to be connected to the internet, so use ethernet for a bit.

After installation, do this in a terminal.

```
sudo apt-get install build-essential
```
Installs build essentials.
```
wget http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6-current.tar.gz
```
Downloads the latest version of Madwifi.
```
tar -zxf madwifi-hal-0.10.5.6-current.tar.gz
```
Extracts Madwifi.
```
cd madwifi-hal-0.10.5.6-r*
```
Moves into the source folder.
```
sudo make
```
```
sudo make install
```
The above two build and install Madwifi.
```
cd
```
```
sudo rm -rf madwifi-hal-*
```
The above two move back to your home directory and remove the nolonger needed compressed folder and source folder.
```
sudo modprobe ath_pci
```
```
sudo reboot
```
The above two add ath_pci (wireless card) to modprobe, and reboots the computer.

You should now be able to configure the network from network manager.

---

