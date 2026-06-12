---
title: "VPN autostart"
date: 2013-12-06
forum: New to Ubuntu
---

### Post by ernie1972 on 2013-12-06
Well finally made the jump to ubuntu 6 months ago, been sorting various things out to get things working but im stumped on this one, i use OPENVPN to connect to the internet, have added a command to startup applications bash -c "sleep 10 && nmcli con up uuid ********************" to autostart my vpn at system boot(found command by searching net). which works great.
However when i close my laptop lid (and it sleeps) when it wakes it wont auto connect to VPN. cant seem to find anything on net to fix this but might be how im wording the search. Using Ubuntu 13.10 desktop if that helps.

---

### Post by gilga2 on 2013-12-26
I've got a similar problem:
I'm using OpenVPN with a script to make it start at startup (I've created a file "myopenvpn" inside /etc/init.d/
> start on runlevel [2345]
stop on runlevel [!2345]
respawn
exec /usr/bin/openvpn --status /var/run/openvpn.client.status 10 --cd /etc/openvpn --config /etc/openvpn/openvpn.conf --syslog openvpn

When I'm using "suspend" (thanks to the command "pm-suspend"), and I wake up my computer after that,  I can't connect to my vpn again.
I have to manually stop the OpenVPN (I see the service working - Apparently, when suspend, OpenVPN loses the connection with the server then) and restart it again.

How to make "pm-suspend" close OpenVPN and restart it again at wake-up?

---

