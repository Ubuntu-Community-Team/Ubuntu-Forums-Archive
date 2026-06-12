---
title: "[SOLVED] wifi networks don't appear in nm-applet"
date: 2008-08-29
forum: New to Ubuntu
---

### Post by joey_breizh on 2008-08-29
Long story short, I uninstalled and reinstalled NetworkManager. I had switched to wcid briefly and was very happy with it but I had too many issues connecting to a VPN...

My problem is that I've reinstalled NetworkManager and if I click on the nm-applet in the taskbar, it doesn't show me all the available wireless networks like it's supposed to. All I have is "Wired Connection" which is unclickable, VPN Connections and Manual Configuration (where I have my wireless network configured but it still won't show or connect).

Am I missing a package or something that would explain the list of wifi connections not showing up when I click on the applet? It used to work fine before I uninstalled NetworkManager.

---

### Post by mlentink on 2008-08-29
Hmmmm

Have you tried right-clicking and enabling wireless networks already?

---

### Post by joey_breizh on 2008-08-29
"Enable networking" is checked, yeah, and that's my only option to check or not.

---

### Post by joey_breizh on 2008-08-29
I was just looking around in the synaptic package manager and two pieces of info that might be of use:

I don't have network-config installed
netapplet either, but when I do install it, it even screws up my wired ethernet connection, so I uninstalled it (too bad because from the description it sounded like it might have fixed the problem)

installing network-config had no positive influence as far as I can tell (I rebooted after installing it) but that might be because it's not configured?

---

### Post by joey_breizh on 2008-08-29
Oh and here is my /etc/network/interfaces file

> auto lo
iface lo inet loopback


iface ath0 inet dhcp
wpa-psk xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
wpa-driver wext
wpa-key-mgmt WPA-PSK
wpa-proto WPA
wpa-ssid firefly

auto ath0

---

### Post by joey_breizh on 2008-08-29
...I have just enabled roaming mode (before I'd manually entered the settings for my wireless connection) and wireless seems to be working again!

Should I thank myself at this point? ;)

---

