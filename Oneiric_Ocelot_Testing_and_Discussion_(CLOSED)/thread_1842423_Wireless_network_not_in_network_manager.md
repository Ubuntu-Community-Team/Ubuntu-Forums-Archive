---
title: "Wireless network not in network manager"
date: 2011-09-11
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by radiognome on 2011-09-11
First I have to congratulate every participant for Oneiric Ocelot Beta-1. Feels and looks beautiful, compared to all previous Unity-instances I have had on my eeepc 900.

But I would not post here if I did not have an issue.

I installed the beta as a fresh install, downloading all the updates using my Wifi as the default network. After the install, my Wifi is not in the Network Manager (saying this device is not managed), so the Wifi-strength meter icon is empty, and Network Manager does nothing for my Wifi.

I do have network connectivity, as in /etc/network/interfaces my Primary Network interface is
auto wlan0
wpa-ssid [my router name]
wpa-psk [the wpa passphrase]

How can I easily revert this so I can use network manager again?

Can this be considered as a bug in the installer or a feature request to have it another way?

Kind regards, Martin

---

### Post by radiognome on 2011-09-11
Consider my issue solved....

I put eth0 als the primary network interface, removed wlan0 from /etc/network/interfaces and rebooted.

Was my first guess to do this, but made a typo in my first try. Then I posted this thread, but could not think of a way why my attempt did not work, so retried.

Leaves my question, Is this a bug in the installer, of is it a feature request to have it altered? I could not explain this to my mother so to say that the wifi-icon is not showing wifi, she can't choose in the menu but still has internet.....

---

### Post by cariboo on 2011-09-12
All I have in /etc/network/interfaces is the following:

> cat /etc/network/interfaces
auto lo
iface lo inet loopback

I have to ask, why if your mother isn't very Ubuntu savvy, is she using pre-released software? 

For the average user, the LTS version is a much better choice, as these sorts of problems don't come up often.

---

