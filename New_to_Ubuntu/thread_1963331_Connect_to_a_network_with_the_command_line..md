---
title: "Connect to a network with the command line."
date: 2012-04-22
forum: New to Ubuntu
---

### Post by john1923 on 2012-04-22
How do I connect to the network using the command line?

I have a server that I want to connect to my home wifi network.

Wifi drivers are installed, ra0 is up, and the lights on the card are working. 

With my ubuntu 10.04 LTS Desktop the network manager does it for me. However the server doesn't seem to have it. The network is WPA-PSK, this should be simple...?

Thank you in advance.

---

### Post by chamber on 2012-04-22
sudo iwconfig wlan0 essid YourNetworkNameHere key 01234567 will work for wep. For wpa you will need wpa supplicant.  

See here

[http://linux.icydog.net/wpa.php](http://linux.icydog.net/wpa.php)

---

### Post by john1923 on 2012-04-22
Thanks for the very quick reply.

This works.

```

sudo ifconfig ra0 up
sudo wpa_passphrase NetworkName "Password" > ~/WifiSetup/wpa_supplicant.conf
sudo wpa_supplicant -B -Dwext -i ra0 -c ~/WifiSetup/wpa_supplicant.conf
sudo dhcpcd ra0

```

---

### Post by chamber on 2012-04-22
No problem. Don't forget to mark your thread as solved.

---

