---
title: "VPN/Proxy/IP changer"
date: 2013-10-21
forum: New to Ubuntu
---

### Post by priscilla2 on 2013-10-21
Hey, guys! I apologize in advance if this question comes up often here. I'm a very beginner using Ubuntu and I'd appreciate any help to keep using it. I usually work with a mac and a windows computer, but now I've decided to install ubuntu on my windows laptop. It's been great so far (I've installed 12.04 precise pangolin). However I travel a lot and often I use some websites and softwares which do not work in the other countries where I've been travelling. 
While using Windows I used FlyVPN and TunnelBear to fake an ip adress in USA or UK (where I currently live).
So, could you guys tell me how can I make the same? I've been searching on google for days and I still didn't find a solution.. maybe my lack of knowledge when it comes to ubuntu..
I appreciate any help!
Thanks! :)

---

### Post by chris137 on 2013-12-16
You go get the server adress (in your case here: [http://www.flyvpn.com/User/VpnServers](http://www.flyvpn.com/User/VpnServers)).
Now you open System->Network and add one by clicking on the '+' below.
VPN should already be checked so you take that, click on next (PPTP should already be checked) and chose a name for the connection (e.g. FlyVPN).
You then copy the server adress you took before into the Gateway-flied.
Username and password of course.
Then you need to klick advanved and there you check Point-to-Point.
Ok -> Save -> Done
To connect you simply click on your network-try-icon (somewhere in the top-right corner of your screen) -> VPN-connections (pretty far below) and choose FlyVPN.

Your connection should establish now.

---

### Post by jimmyh1972 on 2013-12-17
You can use the free proxy list [http://hidemyass.com/proxy-list/](http://hidemyass.com/proxy-list/)
and config your browser
you can use TOR proxy servers
you can use any VPN service that suports linux (hide my ass, astrill, etc.)
the last ones costs money

---

