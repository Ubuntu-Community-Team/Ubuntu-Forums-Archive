---
title: "Wireless driver help, NDISwrappers, and a headache"
date: 2008-11-15
forum: New to Ubuntu
---

### Post by Ikyn on 2008-11-15
So I'm pretty new to Linux in general, and I'm slowly but surely plodding my way through this steep learning curve of GNOME / Ubuntu 8.10. I have my choice between a couple of Wireless PCMCIA cards to use on my new-old laptop:

-Lucent Tech. Orinoco Silver (with side antenna port) 11Mbit/s
-Linksys WPC54G ver 1.2
- 2.4 Ghz OFDM Cardbus Wireless LAN card

That last card looks pretty jenky to me. 

I can get the Orinoco and the last "cardbus?" to work, but I'm confused as to how I use the NDISwrapper to slip in the driver. I also plan on using Kismet at some point, and have an alternative set of drivers for the Orinoco card, but I have no idea how to install them! (They are dragorn's alternative Orinoco drivers directly from his site). 

I've spent the last two days (essentially my entire weekend) scanning through every possible google combination I could think of to gather as much information as possible. Everything I've tried has had little-to-no success. I've re-installed Ubuntu and I'm looking to change these drivers without destroying my system this time.

Any insight would be GREATLY appreciated, as I am syntax-impaired due to my long history using Windows.

Thanks in advance. Cheers!

-Tyson

---

### Post by sirebral on 2008-11-15
I have a Linksys Wireless G USB Adapter. WUSB54G ver. 4

Works great.  I don't even mess with NDIS Wrapper.  i just plugged it in and it works.

---

### Post by Ikyn on 2008-11-15
The card I have is a PCMCIA slot interface, not a USB interface.

---

### Post by shifty_powers on 2008-11-15
you ndisgtk, iirc, which is a gui for ndiswrapper.

you can find ti in synaptic...

---

### Post by Ikyn on 2008-11-15
Thanks! that helps my Linksys question. Now, does anyone have any insight for me on how I can replace the drivers for the Orinoco card that are currently part of the kernal, with the ones I've downloaded from kismetwireless.net?

Thanks again in advance!

---

### Post by sirebral on 2008-11-15
I thought you were looking for something new. My mistake.

---

### Post by alwayshere on 2008-11-15
[http://linuxwireless.org/en/users/Download#DownloadlatestLinuxwirelessdrivers](http://linuxwireless.org/en/users/Download#DownloadlatestLinuxwirelessdrivers)


lotsa wifi info

---

