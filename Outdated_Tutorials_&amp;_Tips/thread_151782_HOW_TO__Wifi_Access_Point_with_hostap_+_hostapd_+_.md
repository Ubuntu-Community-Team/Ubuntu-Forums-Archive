---
title: "HOW TO : Wifi Access Point with hostap + hostapd + freeradius + mysql backend Part 2"
date: 2006-03-28
forum: Outdated Tutorials &amp; Tips
---

### Post by phoboulinos on 2006-03-28
HOW TO : Wifi Access Point with hostap + hostapd + freeradius + mysql backend Part 2 The Return

Configuring clients

Linux

Install wpasupplicant

Note : wpa_supplicant will work only if it supports your card

```


sudo apt-get install wpasupplicant


```


File : /etc/wpa_supplicant/wpa_supplicant.conf should be like this (In breezy I think is in /etc/wpa_supplicant.conf)

```


ctrl_interface=/var/run/wpa_supplicant

eapol_version=1
ap_scan=1
fast_reauth=1


network={
        ssid="MY_SSID"
        key_mgmt=IEEE8021X
        eap=PEAP
        phase2="auth=MSCHAPV2"
        identity="phoboulinos"
        password="supersecret"
}


```


My /etc/network/interface

```


iface eth1 inet static
        address 10.10.10.101
        netmask 255.255.255.128
        gateway 10.10.10.1
        wpa-conf /etc/wpa_supplicant/wpa_supplicant.conf
auto eth1


```

Note: In dapper you may need to load the af_packet module


Windows XP SP2

Open the Properties dialog of your card, go to Wireless Networks tab click Add, enter your ssid in our case the MY_SSID, set Network Authentication to Open, Data encryption to WEP, click the "The key is provided for me automatically". Go to the Authentication tab click on "Enable IEEE 802.1x Authentication" and select Protected EAP (PEAP), click properties, uncheck everything, on "Select Authentication Method:" select EAP-MSCHAP v2, click Configure, you can select to either use your windows logon information to login to the access point or provided a username and password, click accordingly. Also check the "Enable Fast Reconnect". On the MY_SSID properties dialog uncheck the 2 checkboxes "Authenticate as computer when computer information is availiable" and the "Authenticate as geust when user or computer information is unavailible"

Well thats all on Windows.

I hope thats everything 

Have fun

---

