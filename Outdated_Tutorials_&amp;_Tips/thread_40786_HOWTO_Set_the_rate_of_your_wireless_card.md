---
title: "HOWTO: Set the rate of your wireless card"
date: 2005-06-10
forum: Outdated Tutorials &amp; Tips
---

### Post by DaveH on 2005-06-10
The default rate of my wireless card was 1Mb, so this is a quick howto to set it higher for those with the same problem...

In a terminal:
```
iwconfig wlan0
``` 
should give you an output like...
```

wlan0     IEEE 802.11g/b+  ESSID:"Unit 18"  Nickname:"acx100 v0.2.0pre8"
          Mode:Auto  Frequency:2.462 GHz  Access Point: 00:09:5B:6E:4F:9C   
          Bit Rate=1 Mb/s   Tx-Power:15 dBm   Sensitivity=1/3  
          Retry min limit:7   RTS thr:off   
          Power Management:off
          Link Quality=49/100  Signal level=28/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:2  Invalid misc:0   Missed beacon:0

```
with a G card, obviously we'd prefer something closer to 54Mb/s (for B try 11M)
```

sudo iwconfig wlan0 rate 54M

```
If that works fine, then we want the change to be permanent.
```

sudo gedit /etc/network/interfaces

```
Find the section beginning **iface wlan0** and add **up iwconfig wlan0 rate 54M** as the last line. e.g. Mine becomes 
```

iface wlan0 inet static
address 192.168.0.15
netmask 255.255.255.0
gateway 192.168.0.1
wireless-essid Unit 18
up iwconfig wlan0 rate 54M

```
This worked fine for me, I hope you have the same luck!

Cheers
Dave

---

### Post by Sionide on 2005-06-10
Mine's already at 54, why do they limit them!? Seems a bit pointless.

---

### Post by DaveH on 2005-06-10
[QUOTE=Sionide]Mine's already at 54, why do they limit them!? Seems a bit pointless.[/QUOTE]

I'm not sure, but my two cards are ACX100 and ACX111, and use a driver that hasn't had any manufacturer help (cheers Texas Instruments :mad: ).

---

### Post by BoomShake007 on 2005-10-01
Well, this totally screwed up my machine.  I noticed my card, which is a g, was running at 11MBit/s.  so, I did this tutorial to try to get the full potential out of it.  The rate changed, I added that line to the interfaces file, but then problems happened.  As network connection dropped.  It saw the network, but had no connectivity to it.  I had to powercycle my router because it seemed to have crashed (no other computer in the house was getting internet connection).  Now the rest of the computers get connection except this one.

Now, you'll probably say undo it and i'll be fine.  But, now it hangs during boot when it gets to configuring network interfaces.  It just sits there.  I think it crashed the router again as well.  What do i do?

---

### Post by basementjack on 2005-10-22
[QUOTE=BoomShake007]Well, this totally screwed up my machine.  I noticed my card, which is a g, was running at 11MBit/s.  so, I did this tutorial to try to get the full potential out of it.  The rate changed, I added that line to the interfaces file, but then problems happened.  As network connection dropped.  It saw the network, but had no connectivity to it.  I had to powercycle my router because it seemed to have crashed (no other computer in the house was getting internet connection).  Now the rest of the computers get connection except this one.

Now, you'll probably say undo it and i'll be fine.  But, now it hangs during boot when it gets to configuring network interfaces.  It just sits there.  I think it crashed the router again as well.  What do i do?[/QUOTE]

I too got nothing but trouble.. I removed the 'up iwconfig eth1 rate 11M' command from /etc/network/interfaces, but still cannot connect wireless to my router. Only cable is working, am still working on the final solution.

My router did how ever not crash, and are still admitting other devices access to the internet.

Hopefully someone posts a solution, meanwhile I will be fighting the problem.. ;) 

Btw I am using Breezy.

---

