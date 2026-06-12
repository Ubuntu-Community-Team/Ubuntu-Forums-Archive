---
title: "Transmission port forwarding"
date: 2008-05-21
forum: New to Ubuntu
---

### Post by wariskampar on 2008-05-21
Hello, I was Utorrent user for many years but I would like to try Transmission since I just migrated from XP recently. In Utorrent, we can setup the port 'quite' easily but in Transmission I could find such setup. However, in Preference, I could see that the port is open but I'm still confuse because the download speed is only between 30 - 20 kbps whereas while in Utorrent I can easily get 100 over kbps. Torrent file is healthy (20-50 peer)(to be frank I d/load axxo file:)). Do anyone face similar problem and what are the work around?(read "how to port forward")Thanks

---

### Post by aeiah on 2008-05-21
is the port forwarded on your router correctly? does the 'test port' button in transmission tell you its getting through to the outside world? does the site you use block the port you are using?

i havent much experience with transmission. i use deluge, but it should be more or less the same. you might find deluge more similar to utorrent though if you want to give it a try. it wont solve your speed problems though if you havent forwarded correctly.

---

### Post by wariskampar on 2008-05-21
yeah! i second that. main issue now is port forwarding. hope anyone have experience to setup this will assist me. i'm very new in ubuntu. in XP can setup static ip, then setup router. but in ubuntu i'm totally lost

---

### Post by wdaniels on 2008-05-21
> **wariskampar said:**
> in XP can setup static ip, then setup router. but in ubuntu i'm totally lost

You could do the same thing in Ubuntu by setting a static IP in Network Manager (System->Administration->Network), although if your router supports it, UPnP (which allows the client to setup port forwarding automatically in the router) would be the easiest option. I think Deluge supports UPnP, but I don't see it in anywhere in Transmission, albeit only with a brief glance.

Also, note that uTorrent runs quite well under Wine in Linux.

---

### Post by billgoldberg on 2008-05-21
Your ports on the pc should be open by default. 

The only ports you need to forward are the ones on your router.

You would just open firefox and go the the webinterface of the router to do that.

(usually something like: [http://192.168.1.1](http://192.168.1.1))

But I didn't even forwarded my ports on my router, and transmission runs fine for me (400kb/s).

---

### Post by wariskampar on 2008-05-21
in order for me to port forward in router, need to set static ip for my machine first. i'm doing some research on that but if any of you guys can provide quick setup or easy-to-follow instruction, that is much appreciated!

400kbps is very fast indeed!

---

### Post by rhonaldmoses on 2008-09-19
can take the theory part from here...


[http://linuxevangelist.blogspot.com/2007/04/setting-static-ip-for-opensuse-102.html](http://linuxevangelist.blogspot.com/2007/04/setting-static-ip-for-opensuse-102.html)

---

### Post by sonic230584 on 2011-03-24
> **wariskampar said:**
> in order for me to port forward in router, need to set static ip for my machine first. i'm doing some research on that but if any of you guys can provide quick setup or easy-to-follow instruction, that is much appreciated!

400kbps is very fast indeed!



lol not that fast mine downloads at 1.5mbps

---

