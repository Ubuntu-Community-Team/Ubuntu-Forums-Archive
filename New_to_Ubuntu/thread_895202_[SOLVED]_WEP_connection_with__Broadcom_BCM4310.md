---
title: "[SOLVED] WEP connection with  Broadcom BCM4310"
date: 2008-08-19
forum: New to Ubuntu
---

### Post by vikram on 2008-08-19
I can connect to my router without any encryption and with broadcast essid enabled. However when I try WEP it doesnt work. This is the error I see in /var/log/messages

ADDRCONF(NETDEV_UP): wlan0: link is not ready

A few details ...

# uname -r
2.6.24-19-generic

Broadcom Corporation BCM4310 USB Controller

#ndiswrapper -l
bcmwl5 : driver installed
        device (14E4:4315) present (alternate driver: wl)

m# cat /etc/network/interfaces
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0
auto wlan0
iface wlan0 inet dhcp
wireless-essid   112358
wireless-key     5898271111
am I do anything wrong ? I dont want to use an unsecured connection ...

---

### Post by t0p on 2008-08-20
Sorry, I can't answer your query.  I just wanted to warn you: WEP is *not* a secure encryption.  It can be cracked very quickly.  You're better off using WPA.

---

### Post by nicedude on 2008-08-20
I don't see anything that jumps out from what you posted, but I thought I ought to tell you that WEP is in no way secure. I can break a WEP key in less than 5 minutes so I would call it false security. Once you get your problem figured out you might want to try and use WPA with a strong non dictionary password to get pretty tight wifi security. Also choosing a unique ESSID helps if they use WPA rainbow tables to try and crack your WPA key. WEP is better than nothing but I thought I might let you know it is flawed and therefor easily crackable in short amount of time.

Your problem may be in how you entered your WEP key make sure in your router that you copied the key correctly and that you are using the right one, As in when you enter a WEP password in the router it should generate 4 keys from that phrase and you can select which key ( 1-4 ) that you want to use. That key you select is what you need to enter into network manager setup to enable your WEP wifi to work.

Hope this helps you get it figured out and switch to WPA if possible.

---

### Post by vikram on 2008-08-20
to anyone who reads this 

my knetworkmanager configuration was conflicting with the config in /etc/network/interfaces. got rid of my config file and it worked :)

[https://help.ubuntu.com/community/WifiDocs/WPAHowTo/Kubuntu](https://help.ubuntu.com/community/WifiDocs/WPAHowTo/Kubuntu)

---

