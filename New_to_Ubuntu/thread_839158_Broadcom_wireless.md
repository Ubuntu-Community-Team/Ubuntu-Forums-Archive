---
title: "Broadcom wireless"
date: 2008-06-24
forum: New to Ubuntu
---

### Post by jonofan on 2008-06-24
Hey guys, I'm reasonably new to linux. Trying to get my wireless working on my laptop. I have a WPA2-PSK network, which my Desktop on Hardy manages to connect to just fine. 

Laptop is also running Hardy, and can connect to the WEP network which I use at work. It also detects other WPA encrypted networks.

Originally I was using the native driver, which SOMETIMES picked up the network, but could not connect to it. I then followed 
[_this guide_]("http://ubuntuforums.org/showthread.php?t=766560&highlight=alex_kent_18") and can now no longer see the network.

Output from [COLOR="Red"]lspci | grep Broadcom[/COLOR]
```

05:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)
```


Output from [COLOR="Red"]iwconfig[/COLOR]
```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

[COLOR="Red"]ifconfig wlan0 up
iwlist wlan0 scan[/COLOR]

returns no results.


Where do I go from here?

Thanks in advance.

---

### Post by Ryadt on 2008-06-24
Hi...check this tutorial out..
[http://ubuntuforums.org/showthread.php?t=197102&highlight=broadcom](http://ubuntuforums.org/showthread.php?t=197102&highlight=broadcom)

---

### Post by Tomatz on 2008-06-24
There is a problem with wpa2 and some broadcom adaptors in linux (eg you cant connect). Even though its slightly less secure just switch to **wep** in your router config and you should be up and running. If you turn off your ssid broadcast and use mac address filtering you will be even more secure.

---

### Post by jonofan on 2008-06-24
> **Tomatz said:**
> There is a problem with wpa2 and some broadcom adaptors in linux (eg you cant connect). Even though its slightly less secure just switch to **wep** in your router config and you should be up and running. If you turn off your ssid broadcast and use mac address filtering you will be even more secure.

Thanks for the advice. Have tried switching to WEP and even with ssid broadcasting it does not detect the network.

---

### Post by Pjotr123 on 2008-06-24
Try this:
[http://ubuntutip.googlepages.com/nointernetconnection](http://ubuntutip.googlepages.com/nointernetconnection)

---

### Post by jonofan on 2008-06-26
> **Pjotr123 said:**
> Try this:
[http://ubuntutip.googlepages.com/nointernetconnection](http://ubuntutip.googlepages.com/nointernetconnection)


Have followed the above guide installing ndiswrapper. Ndiswrapper says that I already have an installed Windows driver for my broadcom card. 

I have downloaded the windows drivers for my card anyway (which is an exe), but can only add a .inf file. How do I go about getting the .inf file that I need?

---

