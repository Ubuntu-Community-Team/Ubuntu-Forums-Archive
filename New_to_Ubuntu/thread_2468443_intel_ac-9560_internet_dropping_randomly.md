---
title: "intel ac-9560 internet dropping randomly"
date: 2021-10-29
forum: New to Ubuntu
---

### Post by fluffydogbite on 2021-10-29
Hello everyone!

Got Ubuntu yesterday, pretty good so far! But one slight (or giant problem) internet from my intel ac-9560 keeps dropping connection randomly. Is there anyway to fix this or do I need to get a LAN cable?

---

### Post by grahammechanical on 2021-10-29
Hi and welcome.

Some questions. Is the computer dropping the connection to the router/hub? Or is the router/hub dropping the connection to the Internet Service Provider (ISP)? Is your broadband connection to the ISP by telephone land line or by fiber optic cable?

I have a land line connection and for several weeks the download rate was very low and the connection between the router and the ISP would break. The ISP said everything was fine on its part. The telephone company said nothing was wrong with their line. I replaced the router and the problem remained. I was on the point of buying a WiFi dongle to replace the internal WiFi adapter when suddenly the connection started working as it was supposed to work.

I tell you this little story to show that finding the cause is a process of elimination. Using an Ethernet cable would eliminate a weak WiFi connection to the router. Run this command.

```
iwconfig
```

You will see something like this.

> wlx0015af0e9be0  IEEE 802.11  ESSID:"NETGEAR12"  
          Mode:Managed  Frequency:2.447 GHz  Access Point: CC:40 D0:3E:3F:F8   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr: off   Fragment thr: off
          Power Management: off
          Link Quality=54/70  Signal level=-56 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:473  Invalid misc:440   Missed beacon:0


Note the Signal level and the TX-Power level. That might give a clue that the WiFi connection with the router is weak or affected by interference from other WiFi networks that are in range.

Regards

---

### Post by fluffydogbite on 2021-10-29
First, the wifi is dropping from the router to the computer, I know this because I have another computer that is running windows 10 and it runs fine. I think that the router runs a lan line. Oh almost forgot, here.

output from iwconfig:

lo        no wireless extensions.

enp2s0    no wireless extensions.

wlo1      IEEE 802.11  
          Mode:Managed  Frequency:5.24 GHz  Access Point: 6C:AE:F6:4B:61:B1   
          Bit Rate=520 Mb/s   Tx-Power=22 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=35/70  Signal level=-75 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:39   Missed beacon:0

if you can get back to me as soon as possible thanks

---

