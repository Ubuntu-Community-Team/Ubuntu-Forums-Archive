---
title: "Problem In wireless Card Definition"
date: 2011-10-17
forum: New to Ubuntu
---

### Post by woundedbird95 on 2011-10-17
[CENTER]I installed Ubuntu 
My laptop type is
hp-pavilion g6-1105ee

but the wireless network doesn't work

what can i do ??????
[/CENTER]

---

### Post by wesleybishop on 2011-10-17
Make sure the switch for wireless on you laptop is on. Also when you do the install you should plug into Ethernet so that it can do updates and find any necessary drivers.

---

### Post by tasticorp on 2011-10-17
find your wireless adapter first with sudo ifconfig
Is it UP, or is it just network-manager having problems?

The following worked for me in 11.04 with a functioning wifi card that network-manager couldn't make a connection with

sudo stop network-manager
sudo ifconfig wlan0 up            -> wlan0 is the usual location but you need to find the name in the ifconfig output
sudo iwlist wlan0 scan            ->not necessary every time but it will tell you if wlan0 is picking up connections
sudo wpa_passphrase <your_essid> <your_wpa_password > wpa.conf      -> substituting your own network details here, you should only need to do this once
sudo wpa_supplicant -Dwext -iwlan0 -cwpa.conf -B                                   ->this makes your connection, if any of the details earlier are different, adjust accordingly
sudo dhclient wlan0 -b           -> picks up an IP, initially takes 5 min+ but once it's got a valid connection to your router, it will take less, keep an eye on /var/log/syslog to see when you have an IP

If all that works, there's no problem with your card, but network-manager doesn't like it so you will need to find an alternative (e.g. wicd or something similar) to make a connection at login. If it doesn't work, then post back output from ifconfig/iwconfig/dmesg at each step in that process

Note: this is only relevant if you use WPA for your wireless

---

