---
title: "Wireless keeps asking passphrase"
date: 2008-08-25
forum: New to Ubuntu
---

### Post by sheroxe on 2008-08-25
Hi, i just installed ubuntu in my lap and i cant get internet connection. When i click the network icon it shows all the detected wireless networks so i chose mine and it asks for the passphrase, i type it and click 'connect'

Then the icon looks like it's attempting to connect and if i put my mouse over it a dialog says "waiting for network key for the wireless network" and after a while it  pops up again asking for me to type the passphrase again. And no, im not writing the pass wrong.

any idea why?

---

### Post by phidia on 2008-08-25
What type of security do you have? There are [many guides here]("https://help.ubuntu.com/community/NetworkDevices") on setting up networks.
But [this guide]("http://ubuntuforums.org/showthread.php?t=684495") may be more what you're looking for. 
Since you're having a pass phrase issue take a look at the sections on WEP or WPA whichever is your security type.

---

### Post by sheroxe on 2008-08-25
it's a wep security

---

### Post by phidia on 2008-08-25
From the link I inserted previously:

> WEP Connection

You must have either your 64bit or 128 bit HEX Key or the ASCII Equivalent of your HEX Key.

Code:

sudo ifconfig <interface> down
sudo dhclient -r <interface>
sudo ifconfig <interface> up
sudo iwconfig <interface> essid "ESSID_IN_QUOTES"
sudo iwconfig <interface> key HEX_KEY <<<-------- If using ASCII Equivalent, this is s:ASCII_KEY (please make note of the prefix "s:"
****Additional Comand that may be needed  -- sudo iwconfig <interface> key open  <<<----See note below
sudo iwconfig <interface> mode Managed
sudo dhclient <interface>

***The security mode may be open or restricted, and its meaning depends on the card used. With most cards, in open mode no authentication is used and the card may also accept non-encrypted sessions, whereas in restricted mode only encrypted sessions are accepted and the card will use authentication if available.
__________________________________________________ __________________________

Note the prefix mentioned there!

---

### Post by Gone fishing on 2008-08-25
I would try turning roaming off and using the Network manager (System>Administration>network) and setting up your wireless there. 

The config file is /etc/network/interfaces you can check every thing is as it should be.

mine looks like I'm using WEP encryption and a static IP:

to lo
iface lo inet loopback


iface wlan0 inet static
address 192.168.1.224
netmask 255.255.255.0
gateway 192.168.1.1
wireless-key s:qxxxxxxxxxxxx
wireless-essid fish

auto wlan0

the s: before the password shows that the password is an ascii phrase.

---

### Post by sheroxe on 2008-08-25
Thanks i was looking at that in the link, im looking at my connection properties in my pc and it says web encryption but it doesn't say if it's 128 bit passphrase or 64/128 bit hex or 64/128 bit ASCII...how can i know?

Cause in the guide it says "You must have either your 64bit or 128 bit HEX Key or the ASCII Equivalent of your HEX Key" by this they mean my pass?

---

### Post by sheroxe on 2008-08-25
[QUOTE=Gone fishing;5661319]I would try turning roaming off and using the Network manager (System>Administration>network) and setting up your wireless there. QUOTE]


oh that worked fine, thanks :D

---

### Post by beeray on 2008-10-27
> **sheroxe said:**
> [QUOTE=Gone fishing;5661319]I would try turning roaming off and using the Network manager (System>Administration>network) and setting up your wireless there. QUOTE]


oh that worked fine, thanks :D

im having the same problem, how do you turn roaming off??

---

