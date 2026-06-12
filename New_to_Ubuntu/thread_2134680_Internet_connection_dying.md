---
title: "Internet connection dying?"
date: 2013-04-11
forum: New to Ubuntu
---

### Post by roseysdaddy on 2013-04-11
Im having an issue with my Ubuntu Server 12.04 machine killing my internet connection over time.  It's been running for four days and I've noticed when I wake up Ive had to reboot my router each morning.  Im currently just using the server for Deluge/torrenting but plan on setting up minidlna in the future.  Before, using my laptop and utorrent and being a heavy torrent user, I had not once rebooted the router, so Im sure the issue is with the server.

What I need to do is figure out how to track down if it's Deluge or Ubuntu that is the issue.   My router is an ASUS RT&#8209;N66U and the machine is connected via cat5 cable, so Im pretty solid that its not because it's and old/outdated router.

Edit:  Nevermind.  Ill just kill deluge and see how things work in the morning.

---

### Post by DuckHook on 2013-04-12
Don't be so quick to absolve your router because the problem may indeed be with it and not your computer or software. I know nothing about your actual router model, but it is very possible that your router is choking on the large number of separate IP connections and port usage that are created through torrenting. You may wish to Google both maximum ports and TCP/UDP Timeout to establish what settings are best for torrenting with your router model, then set both settings to the recommended ones.

Your router documentation may also give you the best settings for torrenting. You can also restrict the number of peers in your torrents to reduce the port load on your router. This is likely the only option you have if your router does not allow for tweaking (in your case, restricting) of the maximum ports and timeouts.

---

### Post by roseysdaddy on 2013-04-13
I may be 100% wrong, but my guts says it's not router.  

Ive had it for over a year and used a windows xp machine to torrent 24/7 during that time.  I didn't have to reboot d/t the router being overwhelmed at all during that period.  

But if there is some setting or some other thing I could try, I'd love to try anything.

---

### Post by DuckHook on 2013-04-14
That depends on what your settings were in WinXP. Were you running 60 peers per torrent? How many torrents at one time?

If you are running many torrents with many peers each, the number of ports grows geometrically.

As mentioned, if you don't want to touch your router, try cutting down the number of torrents and limiting peers to a lower number than the default (which I believe is 60).

---

