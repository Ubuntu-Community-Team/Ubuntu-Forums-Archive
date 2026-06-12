---
title: "Bittorrent clients make the internet stop working."
date: 2012-06-27
forum: New to Ubuntu
---

### Post by milton0523 on 2012-06-27
Hey, so whenever I try to run a torrent client, the internet just stops working. The internet light on the modem turns red and nothing works until it reconnects 10 seconds later. It downloads a bit, then stops working again. I have another (windows) computer, and bittorrent works fine on it. I have a Toshiba NB505 with the most recent distribution (12.10, I think), I have tried all the clients in the software center, and i have AT&T internet. Please help. :icon_frown:

---

### Post by carl4926 on 2012-06-27
we better see the result of

cat /etc/lsb-release

---

### Post by HiImTye on 2012-06-27
at&t wireless internet (from, for instance, a cell phone or stick) or at&t broadband type internet?

---

### Post by milton0523 on 2012-07-24
sorry i couln't reply

I got 
```

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04 LTS"
```

And I have Wireless DSL.

---

### Post by Bufeu on 2012-07-24
Maybe the modem gets overloaded? Try to reduce the maximum number of connections in your BitTorrent-client. If you're using Transmission, take a look [here]("https://trac.transmissionbt.com/wiki/EditConfigFiles").

---

### Post by DarkAmbient on 2012-07-24
If you're able to access our modem over telnet or similary in a console, you might be able to downclock (or overclock) it's cpu. That worked for me on my (gigabits)router who passed out as soon as there was a lot of internet activity. Tweaked it from 350mzh to 300mhz.

No idea if it will help you though.. just a thought.

---

### Post by milton0523 on 2012-07-24
> **Bufeu said:**
> Maybe the modem gets overloaded? Try to reduce the maximum number of connections in your BitTorrent-client. If you're using Transmission, take a look [here]("https://trac.transmissionbt.com/wiki/EditConfigFiles").

I tried to do that, but it goes out from just having the program on, not doing anything.

@DarkAmbient

I don't know what most of those words mean, but i know it won't work. I have a windows computer that can download torrents fine at full speed.

---

### Post by Cheesehead on 2012-07-24
Bufeu and DarkAmbient are right - the symptoms you describe are a classic router inability to handle torrents at max speed or max connections. Torrent clients in the Ubuntu repos all handle torrents the standard way, so switching clinets is unlikely to change anything.

Make sure your upload/download and max connection limits *exactly* match those of your windows client, and you are certain to get similar behavior from the router.

I've used various torrent clients for many years, and the problem has *never* been the torrent client. Sometimes it's the tracker, sometimes it's a user mistake, but most often it's a cheap router choking on too many connections. Now I use Ubuntu for my router OS, too, and it's smoother than Linksys and D-Link ever were.

---

