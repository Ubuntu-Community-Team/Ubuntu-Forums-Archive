---
title: "Atheros, Again"
date: 2008-08-03
forum: New to Ubuntu
---

### Post by jsudekum on 2008-08-03
So, I'm COMPLETELY new to Ubuntu and Linux in general. I just installed Hardy on my girlfriend's Compaq Presario C700 and am having a balls time trying to get the Atheros wireless to work. Everything else is fly, but this has been eluding me...

I've tried this: [http://www.ubuntugeek.com/atheros-ar5007-wireless-with-madwifi-on-ubuntu-804-hardy-heron.html](http://www.ubuntugeek.com/atheros-ar5007-wireless-with-madwifi-on-ubuntu-804-hardy-heron.html)

But with no result. The computer isn't recognizing a signal at all... So, what should I do?

iwconfig: o        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-96 dBm  Noise level=-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


Thanks for the help. Anything is appreciated.

---

### Post by Bachstelze on 2008-08-03
Please open a terminal (Applications > Accessories > Terminal), do a [font="Courier New"]lspci -nn[/code] ans paste the output.

---

