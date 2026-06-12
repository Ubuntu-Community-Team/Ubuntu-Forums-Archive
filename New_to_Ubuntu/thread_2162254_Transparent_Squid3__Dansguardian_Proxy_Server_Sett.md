---
title: "Transparent Squid3 / Dansguardian Proxy Server Settings"
date: 2013-07-13
forum: New to Ubuntu
---

### Post by gorgeousgorge on 2013-07-13
[SIZE=1] [COLOR=#00000a][FONT=Tahoma, serif]Hi[/FONT][/COLOR]
[/SIZE]
[SIZE=1] [/SIZE][SIZE=1] 
[/SIZE]
[SIZE=1] [/SIZE][SIZE=1] [COLOR=#00000a][FONT=Tahoma, serif]Very new to Ubuntu and hoping someone can point out my school boy mistake. I've managed to get Squid3 and Dansguardian working fine as a proxy server hanging off a switch with the rest of my network (configuring Firefox / MS Explorer proxy settings).[/FONT][/COLOR][/SIZE]
[SIZE=1] [/SIZE][SIZE=1] 
[/SIZE]
[SIZE=1] [/SIZE][SIZE=1] [COLOR=#00000a][FONT=Tahoma, serif]I'm trying to find out what settings are different between that and a transparent proxy server between router and switch. I've got two network cards eth0 connecting to my router (router providing dhcp but with with reserved mac to ip addresses for all devices including the proxy server) and eth1 connecting to my switch with everything else on the network hanging off it.[/FONT][/COLOR][/SIZE]

[SIZE=1] [/SIZE][SIZE=1] 
[/SIZE]
[SIZE=1] [/SIZE][SIZE=1] [COLOR=#00000a][FONT=Tahoma, serif]Installed Webmin / Squid3 / SARG / DansGuardian...[/FONT][/COLOR][/SIZE]
[SIZE=1] [/SIZE][SIZE=1] 
[/SIZE]
[SIZE=1] [/SIZE][SIZE=1] [COLOR=#00000a][FONT=Tahoma, serif]Webmin works fine.[/FONT][/COLOR][/SIZE]
[SIZE=1] [/SIZE][SIZE=1] [COLOR=#00000a][FONT=Tahoma, serif]Squid3 works fine.[/FONT][/COLOR][/SIZE]
[SIZE=1] [/SIZE][SIZE=1] [COLOR=#00000a][FONT=Tahoma, serif]SARG works fine.[/FONT][/COLOR][/SIZE]
[SIZE=1] [/SIZE][SIZE=1] [COLOR=#00000a][FONT=Tahoma, serif]Dansguardian doesn't log anything in this file after generating internet traffic from my network;[/FONT][/COLOR][/SIZE]
[SIZE=1] [/SIZE][SIZE=1] [COLOR=#00000a][FONT=Tahoma, serif]loglocation = '/var/log/dansguardian/access.log' [/FONT][/COLOR] [/SIZE]
[SIZE=1] [/SIZE][SIZE=1] 
[/SIZE]
[SIZE=1] [/SIZE][SIZE=1] [COLOR=#00000a][FONT=Calibri, serif][FONT=Tahoma, serif]I've set up a bridge for internet traffic which is working in [/FONT][FONT=Courier New, serif][FONT=Tahoma, serif]/etc/network/interfaces:[/FONT][/FONT][/FONT][/COLOR][/SIZE]
[SIZE=1] [/SIZE][SIZE=1] [COLOR=#00000a][FONT=Calibri, serif][FONT=Courier New, serif][FONT=Tahoma, serif]auto lo 
iface lo inet loopback 
sudo gedit /etc/network/interfaces [/FONT][/FONT][/FONT][/COLOR] [/SIZE]
[SIZE=1] [/SIZE][SIZE=1] [COLOR=#00000a][FONT=Tahoma, serif]iface eth0 inet manual[/FONT][/COLOR][/SIZE]
[SIZE=1] [/SIZE][SIZE=1] [COLOR=#00000a][FONT=Tahoma, serif]iface eth1 inet manual[/FONT][/COLOR][/SIZE]
[SIZE=1] [/SIZE][SIZE=1] [COLOR=#00000a][FONT=Tahoma, serif]auto brAdrian[/FONT][/COLOR][/SIZE]
[SIZE=1] [/SIZE][SIZE=1] [COLOR=#00000a][FONT=Tahoma, serif]iface brAdrian inet dhcp[/FONT][/COLOR][/SIZE]
[SIZE=1] [/SIZE][SIZE=1] [COLOR=#00000a][FONT=Tahoma, serif]bridge_ports eth0 eth1[/FONT][/COLOR][/SIZE]
[SIZE=1] [/SIZE][SIZE=1] [COLOR=#00000a][FONT=Tahoma, serif]ip route add default via 192.168.0.1[/FONT][/COLOR][/SIZE]
[SIZE=1] [/SIZE][SIZE=1] [COLOR=#00000a][FONT=Tahoma, serif]dhclient brAdrian[/FONT][/COLOR][/SIZE]
[SIZE=1] [/SIZE][SIZE=1] 
[/SIZE]
[SIZE=1] [/SIZE][SIZE=1] [COLOR=#00000a][FONT=Tahoma, serif]Made these changes to /etc/dansguardian/dansguardian.conf[/FONT][/COLOR][/SIZE]
[SIZE=1] [/SIZE][SIZE=1] [COLOR=#00000a][FONT=Tahoma, serif]#'d - UNCONFIGURED - Please remove this line after configuration[/FONT][/COLOR][/SIZE]
[SIZE=1] [/SIZE][SIZE=1] [COLOR=#00000a][FONT=Tahoma, serif]logfileformat = 3[/FONT][/COLOR][/SIZE]
[SIZE=1] [/SIZE][SIZE=1] [COLOR=#00000a][FONT=Tahoma, serif]Un#'d - loglocation = '/var/log/dansguardian/access.log'[/FONT][/COLOR][/SIZE]

[SIZE=1] [/SIZE][SIZE=1] 
[/SIZE]
[SIZE=1] [/SIZE][SIZE=1] [COLOR=#00000a][FONT=Tahoma, serif]Made these changes to /etc/squid3/squid.conf with a 500Gb disk drive mounted @ /cache[/FONT][/COLOR][/SIZE]
[SIZE=1] [/SIZE][SIZE=1] [COLOR=#00000a][FONT=Tahoma, serif]visible_hostname BedsonProxyServer [/FONT][/COLOR] [/SIZE]
[SIZE=1] [/SIZE][SIZE=1] [COLOR=#00000a][FONT=Tahoma, serif]Un#'d - acl localnet src 192.168.0.0/16[/FONT][/COLOR][/SIZE]
[SIZE=1] [/SIZE][SIZE=1] [COLOR=#00000a][FONT=Tahoma, serif]cache_dir ufs cache_dir ufs /cache 481280 16 256 [/FONT][/COLOR] [/SIZE]
[SIZE=1] [/SIZE][SIZE=1] [COLOR=#00000a][FONT=Tahoma, serif]http_port 3128 transparent[/FONT][/COLOR][/SIZE]

[SIZE=1] [/SIZE][SIZE=1] [COLOR=#00000a][FONT=Tahoma, serif]always_direct allow all[/FONT][/COLOR][/SIZE]
[SIZE=1] [/SIZE][SIZE=1] 
[/SIZE]
[SIZE=1] [/SIZE][SIZE=1] [COLOR=#00000a][FONT=Tahoma, serif]Made this change to /etc/sarg/sarg.conf[/FONT][/COLOR][/SIZE]
[SIZE=1] [/SIZE][SIZE=1] [COLOR=#00000a][FONT=Tahoma, serif]access_log /media/dansguardian/logs/access.log[/FONT][/COLOR][/SIZE]
[SIZE=1] [/SIZE][SIZE=1] 
[/SIZE]
[SIZE=1] [/SIZE][SIZE=1] [COLOR=#00000a][FONT=Calibri, serif][FONT=Tahoma, serif]Made a link b[/FONT]*[COLOR=#00000a][FONT=Tahoma, serif]etween Squid and Dansguardian (trying everything I could think of!) and saved it[/FONT][/COLOR]*[/FONT][/COLOR][/SIZE]
[SIZE=1] [/SIZE][SIZE=1] [COLOR=#00000a][FONT=Calibri, serif]*[COLOR=#00000a][FONT=Tahoma, serif]sudo iptables -t nat -A PREROUTING -i eth0 -p tcp --dport 3128 -j REDIRECT --to-port 8080[/FONT][/COLOR]*[/FONT][/COLOR][/SIZE]
[SIZE=1] [/SIZE][SIZE=1] [COLOR=#00000a][FONT=Calibri, serif]*[COLOR=#00000a][FONT=Tahoma, serif]sudo iptables -t nat -A PREROUTING -i eth1 -p tcp --dport 3128 -j REDIRECT --to-port 8080[/FONT][/COLOR]*[/FONT][/COLOR][/SIZE]
[SIZE=1] [/SIZE][SIZE=1] [COLOR=#00000a][FONT=Calibri, serif]*[COLOR=#00000a][FONT=Tahoma, serif]sudo iptables -t nat -A PREROUTING -i brAdrian -p tcp --dport 3128 -j REDIRECT --to-port 8080[/FONT][/COLOR]*[/FONT][/COLOR][/SIZE]
[SIZE=1] [/SIZE][SIZE=1] [COLOR=#00000a][FONT=Calibri, serif]*[COLOR=#00000a][FONT=Tahoma, serif]sudo sh -c "iptables-save > /etc/iptables.rules"[/FONT][/COLOR]*[/FONT][/COLOR][/SIZE]
[SIZE=1] [/SIZE][SIZE=1] 
[/SIZE]
[SIZE=1] [/SIZE][SIZE=1] [COLOR=#00000a][FONT=Calibri, serif]*[COLOR=#00000a][FONT=Tahoma, serif]Still nothing in /var/log/dansguardian/access.log, my assumption is that the intranet traffic from my network is hitting Squid3 (I can see the stored files in /cache) BUT not hitting Dansguardian.[/FONT][/COLOR]*[/FONT][/COLOR][/SIZE]
[SIZE=1] [/SIZE][SIZE=1] 
[/SIZE]
[SIZE=1] [/SIZE][SIZE=1] [COLOR=#00000a][FONT=Calibri, serif]*[COLOR=#00000a][FONT=Tahoma, serif]Any help would be very much appreciated!!![/FONT][/COLOR]*[/FONT][/COLOR][/SIZE]
[SIZE=1] [/SIZE][SIZE=1] 
[/SIZE]
[SIZE=1] [/SIZE][SIZE=1] [COLOR=#00000a][FONT=Calibri, serif]*[COLOR=#00000a][FONT=Tahoma, serif]Thanks[/FONT][/COLOR]*[/FONT][/COLOR][/SIZE]
[SIZE=1] [/SIZE][SIZE=1] 
[/SIZE]
[SIZE=1] [/SIZE][SIZE=1] [COLOR=#00000a][FONT=Calibri, serif]*[COLOR=#00000a][FONT=Tahoma, serif]Adrian[/FONT][/COLOR]*[/FONT][/COLOR][/SIZE]

---

### Post by gorgeousgorge on 2013-07-17
OK, solved it, so my fullguide to how to install a transparent proxy / dansguardian filtering server between router and switch is here ... [https://mega.co.nz/#!uQgHFaQT!Omnhyw0zAOJjdkEe44rsqUSST4IJtZwkMUnPgOmjII8](https://mega.co.nz/#!uQgHFaQT!Omnhyw0zAOJjdkEe44rsqUSST4IJtZwkMUnPgOmjII8)

Hope it helps someone...

Cheers

Adrian

---

### Post by andytof472 on 2013-08-16
Hey Gorge,

I just tried to click the link for the setup guide and it's dead. Any chance of putting it back up

Cheers

---

