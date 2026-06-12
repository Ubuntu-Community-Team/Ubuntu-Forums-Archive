---
title: "connections allowed only via vpn"
date: 2012-02-23
forum: New to Ubuntu
---

### Post by lorenzo0523 on 2012-02-23
Hi all,
I would like to know if there is a way (maybe using a firewall setting or something else) to connect to the internet only through vpn or to block any kind of connection if the vpn suddenly stops working (it happens many times a day). I tried many times but I'm a newbie. I use a vpn service which gave me an id, a password and an address. I set up the connection and that's all right, but if the vpn connection falls, I found that I'm still connected through the internet with my ip and not protected by the vpn one... I hope I made clear the point..
thanks

---

### Post by d4m1r on 2012-02-23
I don't believe this is possible in 11.04 or 11.10 using the default Network Manager. When you are connected to the VPN, it routes all traffic over it by default, but when it disconnects, it uses your regular internet connection.

I'd almost say unplugging the cable when VPN is disconnected is the best option if you don't want to use your regular internet connection for whatever reason. Maybe you could find more options in your routers admin panel? (set VPN info as default so when it disconnects you won't get internet).

---

