---
title: "MPD client configuration"
date: 2011-11-01
forum: New to Ubuntu
---

### Post by tomek5577 on 2011-11-01
Hello everybody :)
I'm running newest distro of Lubuntu, but I think that kind of distribution doesn't metter now.

I'm trying to configure MPD on laptop with lubuntu [server] and have remote control from another laptop with windows [GMPC] and iPhone [MPoD]. The problem is, that MPD seems to be ok (sonata on server notebook works well), but client on any other machine can't connect to server. I tried a lot of options in config file of MPD (including commenting out "bind to adress" and "port", changing adress to "localhost" and changing all this values). Client on different machine than server is still unable to connect. All devices are connected to network wirelessly by Netgear DG834G.

I'm after 3 days of trying everything and looking for answer. Please help :) Sorry for my english :)

---

### Post by brianw0667 on 2011-11-03
I was just trying to do the same thing. You have to change the value of the bind address to be the IP address. 

bind_to_address         "192.168.2.99"

This allowed me to connect to the server from my laptop. I have the web based relaxx player installed and it lost connection so I will need to look into it to get it to use the IP address instead of localhost and any client that is on the server will now need to use the IP address instead of localhost.

[edit]
I checked the relaxx config and changed it to the servers IP address and it connected again so each client will need to use the IP address instead of the local host address. May also be able to just make a change in /etc/hosts but have not looked into that yet.

---

