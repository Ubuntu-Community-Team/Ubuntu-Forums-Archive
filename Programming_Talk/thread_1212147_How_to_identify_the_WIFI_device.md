---
title: "How to identify the WIFI device?"
date: 2009-07-13
forum: Programming Talk
---

### Post by pokerbirch on 2009-07-13
I'm scripting the "iwconfig" and "airmon-ng" start/stop commands with Python. My script currently calls iwconfig and parses the output to make a list of active devices. It then uses that list to send the "airmon-ng stop xxx" command to each device. So now iwconfig returns:
```
lo       no wireless extensions.
eth1     no wireless extensions.
wifi0    no wireless extensions.
```
Now i need to restart one of the devices in monitor mode. That is a simple call to "airmon-ng start xxx", but WHICH device? I obviously know that i should use "wifi0" but how would my script make that decision? Is there another command i can call to identify wifi0 as my wifi device? "wifi0" could be hard-coded, but, for instance, my desktop pc names the wifi device "wlan0" which would obviously render the script useless.


EDIT:
A possible solution would be to loop through the list of devices, issuing the "airmon-ng start" command to each one until we get a "(monitor mode enabled)" output and/or reach the end of the list. Would there be any problems in doing this?

---

### Post by Martin Witte on 2009-07-13
when you have a wireless connection *iwconfig* prints  something like

```
martin@toshibap200:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

ath0      IEEE 802.11bg  ESSID:"SX551D431D8"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:01:E3:D4:31:D8   
          Bit Rate=24 Mb/s   Tx-Power=20 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=48/100  Signal level:-64 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

martin@toshibap200:~$ 
```

so in my case ath0 is the wireless interface. Your output doesn't show a wireless interface. An alternative command you can consider is *iwgetid*

```
martin@toshibap200:~$ iwgetid
ath0      ESSID:"SX551D431D8"
martin@toshibap200:~$ 

```

see [this]("http://en.wikipedia.org/wiki/Wireless_tools_for_Linux") page as well for some more info on Linux wireless

---

### Post by pokerbirch on 2009-07-13
Yes, that is correct. After i have stopped all wireless devices with the "airmon-ng stop" command my listing is correct. **ath0** only appears after i run "airmon-ng start wifi0" which is also correct behaviour. In order to put a wifi device into "monitor" mode, you have to stop it and then restart it which is why i am scripting the commands. What i am asking is: how can i make my script identify that it should use "wifi0" rather than "lo" or "eth1" when issuing the "airmon-ng start" command?

The only solution i have so far is to loop through all the devices until i get an output containing "monitor mode enabled". It's a bit kludgy, but it works. I was hoping there might be a cleaner way...

---

### Post by soltanis on 2009-07-13
Use the one named wifi0. That seems to be how your driver enables the device. Other drivers behave differently: my wireless card is named wlan0.

---

### Post by pokerbirch on 2009-07-13
> **soltanis said:**
> Use the one named wifi0. That seems to be how your driver enables the device. Other drivers behave differently: my wireless card is named wlan0.

Yes, but hard coding it as "wifi0" is not much use on a different pc...

---

### Post by soltanis on 2009-07-13
Yes, but I notice that for the most part, wireless interfaces have a "w" in the first position. I suggest you use this as a heuristic to pick a card that looks like it would be a wireless card first, then if that fails, cycle through the rest using the brute force method.

---

### Post by Martin Witte on 2009-07-14
> **soltanis said:**
> Yes, but I notice that for the most part, wireless interfaces have a "w" in the first position. I suggest you use this as a heuristic to pick a card that looks like it would be a wireless card first, then if that fails, cycle through the rest using the brute force method.

Mine is **ath0**, so it wouldn't be detected under this rule

---

### Post by tturrisi on 2009-07-14
Have a look at airoscript to see how to detect the interface on the system:
[http://airoscript.aircrack-ng.org/](http://airoscript.aircrack-ng.org/)

---

