---
title: "Wpa_supplicant keeps alternating connect/disconnect"
date: 2011-11-03
forum: New to Ubuntu
---

### Post by Maverick1 on 2011-11-03
Hi all,

I am somewhat new to Ubuntu/Linux. At the moment, i have a  python script which attempts to connect to a wireless network via  terminal using "wpa_passphrase" and "wpa_supplicant" commands.

- I have configured my "/etc/network/interfaces" file to look like this:

auto wlan0
iface wlan0 inet dhcp
    wpa-ssid 'my ssid'
    wpa-psk 'my psk'

- These are the commands i use to create and run my wpa_sup.conf file:

"wpa_passphrase 'my ssid' 'my psk' > wpa_sup.conf"
     and
"wpa_supplicant -Dwext -iwlan0 -cwpa_sup.conf"

I do connect to the network with these commands, but it constantly connects and disconnects. OUTPUT BELOW:

CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
ioctl[SIOCGIWSCAN]: Resource temporarily unavailable
ioctl[SIOCSIWSCAN]: Device or resource busy
Failed to initiate AP scan.
Trying to associate with c8:bc:c8:fe:97:a9 (SSID='Artemis WN' freq=2462 MHz)
Associated with c8:bc:c8:fe:97:a9
WPA: Key negotiation completed with c8:bc:c8:fe:97:a9 [PTK=CCMP GTK=CCMP]
CTRL-EVENT-CONNECTED - Connection to c8:bc:c8:fe:97:a9 completed (auth) [id=0 id_str=]
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
ioctl[SIOCSIWSCAN]: Device or resource busy
Failed to initiate AP scan.
Trying to associate with c8:bc:c8:fe:97:a9 (SSID='Artemis WN' freq=2462 MHz)
Associated with c8:bc:c8:fe:97:a9
WPA: No SSID info found (msg 1 of 4).
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
ioctl[SIOCSIWSCAN]: Device or resource busy
Failed to initiate AP scan.
Trying to associate with c8:bc:c8:fe:97:aa (SSID='Artemis WN' freq=5180 MHz)
Associated with c8:bc:c8:fe:97:aa
WPA: Key negotiation completed with c8:bc:c8:fe:97:aa [PTK=CCMP GTK=CCMP]
CTRL-EVENT-CONNECTED - Connection to c8:bc:c8:fe:97:aa completed (reauth) [id=0 id_str=]
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
ioctl[SIOCSIWSCAN]: Device or resource busy
Failed to initiate AP scan.
Trying to associate with c8:bc:c8:fe:97:aa (SSID='Artemis WN' freq=5180 MHz)
Associated with c8:bc:c8:fe:97:aa
WPA: Key negotiation completed with c8:bc:c8:fe:97:aa [PTK=CCMP GTK=CCMP]
CTRL-EVENT-CONNECTED - Connection to c8:bc:c8:fe:97:aa completed (reauth) [id=0 id_str=]
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
ioctl[SIOCSIWSCAN]: Device or resource busy
Failed to initiate AP scan.

I've  searched far and wide for a solution or any help about this; a lot of  people have posted about this same problem and i've also tried almost  everything that i've come across to fix this. From what i see, i'm  almost fully connected.. Any help would be appreciated as to why the  connect/disconnect alternating!

:smile:

---

### Post by anewguy on 2011-11-03
A brief scan of the net indicates this may be specific to a certain wireless card.

Please do the following:

lspci > dwetemp.txt

lsusb >> dwetemp.txt

ifconfig >> dwetemp.txt

iwconfig >> dwetemp.txt

lsmod >> dwetemp.txt

Then, post a message back here and attach the file dwetemp.txt.

Did you do anything to load a driver for your wireless or did it just attempt to work right out of the box?

Also - what version of Ubuntu and on what platform?

Thanks!
Dave ;)

---

### Post by Maverick1 on 2011-11-04
Hey Dave,

I have attached the "dwetemp.txt" file to this reply as requested.

I haven't done anything to load a driver, i've recently just installed the wireless card and it worked right out of the box.

Also, i am working in Linux Ubuntu 2.6.



Thanks!

PS: as i'm working on my computer, i repeatedly get notifications saying "connection established" and "disconnected"...

---

### Post by anewguy on 2011-11-06
Have you tried reverting everything back to the way it was before you modified anything (like /etc/network/interfaces and wpa_sup.conf) and then just letting the network manager ask for the network password/passphrase (it will only do this once unless you clear it at some point in the future).  This is how most of us do it - just click the network, answer the prompt, let it connect, and usually from then on it will just auto-connect to the network when ever it is in range, including on boot.  You should only have to select the network and enter the password/phrase once unless you modify it later or you connect to another network and then want to reconnect to the original network.

Dave ;)

---

### Post by Maverick1 on 2011-11-07
Well the thing is, i CAN connect if i just select a network from NetworkManager and enter a passphrase which it remembers for future attempts to connect. But the task i am trying to accomplish for my project is to successfully connect to a network through a Python script by running terminal commands such as 'wpa_passphrase' and 'wpa_supplicant'.

Connecting straight through Network Manager does establish a connection which maintains a consistent connection to the network. But when i run ' sudo wpa_supplicant -Dwext -iwlan0 -cwpa_sup.conf' to connect to a network with it's passphrase, i get either this:

Trying to associate with c8:bc:c8:fe:97:a9 (SSID='Artemis WN' freq=2462 MHz)
Associated with c8:bc:c8:fe:97:a9
WPA: 4-Way Handshake failed - pre-shared key may be incorrect
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Trying to associate with c8:bc:c8:fe:97:a9 (SSID='Artemis WN' freq=2462 MHz)
Associated with c8:bc:c8:fe:97:a9
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Trying to associate with c8:bc:c8:fe:97:a9 (SSID='Artemis WN' freq=2462 MHz)
Associated with c8:bc:c8:fe:97:a9
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Trying to associate with c8:bc:c8:fe:97:a9 (SSID='Artemis WN' freq=2462 MHz)
Associated with c8:bc:c8:fe:97:a9
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys

OR: what i pasted in the initial post where it connects and disconnects repeatedly


I've been trying to find out what "CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys" means but no luck..

---

