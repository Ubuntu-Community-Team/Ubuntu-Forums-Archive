---
title: "Wireless router restarts when I connect to it since installing Ubunutu 11.10 beta"
date: 2011-10-01
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by tastygroove on 2011-10-01
This is a strange problem and I have no idea what might be causing it, but since installing the Oneiric beta my wireless router resets every time I connect with my laptop.  Actually, I can connect and get Internet access for a few seconds and it resets.  And the router does actually reset.  All of the lights on the router shut off and it goes through it's boot up process.  

This was not a problem with 11.04.  It is also not a problem with the Live CD for Oneiric.

I have a Dell Latitude E6510.  I don't know what information I should report.  I'll list what I know.  I'm sure it's inadequate.  I can't provide more info by request.

lspci

```

...
02:00.0 Network controller: Intel Corporation Centrino Advanced-N 6200 (rev 35)
...

```

iwconfig

```

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"WLAN-C5E224"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:26:4D:C5:E2:1A   
          Bit Rate=11 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-30 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:28   Missed beacon:0

```

Does anyone have any ideas?  I'm completely lost here.

---

### Post by pressureman on 2011-10-01
You didn't specify what type of router you have. Have you tried searching for a firmware update for it?

I've experienced similar problems with consumer grade WiFi routers (in my case, a Zyxel router supplied by Vodafone in Germany), and it usually comes down to flaky firmware on them.

---

### Post by BigCityCat on 2011-10-01
Looking at the front page of tells me there are currently network problems with oneiric.

---

### Post by tastygroove on 2011-10-01
> You didn't specify what type of router you have. Have you tried searching for a firmware update for it?

You're right, I didn't.  Sorry about that.  I have a Speedport W 722V supplied by Deutsche Telekom in Germany.  I have the most recent firmware installed (v 1.18 ) and the problem persists.

I just found a bug report that someone has already issued for this exact problem.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/821157](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/821157)

---

### Post by obriente on 2011-10-01
Try adding "options iwlagn 11n_disable=1" to your /etc/modprobe.d/iwlagn.conf file. Worked for me. Not ideal, but better than not having a router.

---

### Post by prettyboy85712 on 2011-10-13
I'm currently experiencing this same issue with my Dell Studio 1749. What a pain especially when it works fine in Natty.

---

