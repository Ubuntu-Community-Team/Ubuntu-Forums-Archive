---
title: "Squid Transparent proxy settings"
date: 2009-02-27
forum: Philippine Team
---

### Post by zanda on 2009-02-27
Guys ask ko lang po ang opinions, experience anything you can share...

First share ko lang po ito, again, I'd like to promote UBUNTU SERVER's sa office namin :guitar:, since part ako ng I.T. administration, First Project po namin is our FTP server, before it was running on Windows, and luckily I convinced them that we try UBUNTU SERVER, and so far , it was doing good , wala pang major problem na na e-encounter. :D

So, ngayon na po, we are planning on a web cache proxy server, since our Office is frequently visiting certains sites, 

"SQUID as a proxy server", gusto kasi namin gawin set-up is TRANSPARENT para hindi na po namin configure pa yung mga users on their part to change their setting para sa proxy server, if ever po ba ganito ang set-up namin and nagka problem itong proxy namin, automatic pa rin ba na mawawalan ng internet ang mga users namin...kasi kung yung normal settings lang po ng proxy, once mag down yung proxy automatic down din ang browsing tama po ba, so yun po ang gusto namain maiwasan, maiiwasan po ba to kung se-setup namin as transparent.


Thanks in Advance

---

### Post by loell on 2009-02-28
try this tutorial
[transparent squid proxy]("http://www.ubuntugeek.com/how-to-setup-transparent-squid-proxy-server-in-ubuntu.html")

---

### Post by badrra on 2009-06-01
> **zanda said:**
> Guys ask ko lang po ang opinions, experience anything you can share...

First share ko lang po ito, again, I'd like to promote UBUNTU SERVER's sa office namin :guitar:, since part ako ng I.T. administration, First Project po namin is our FTP server, before it was running on Windows, and luckily I convinced them that we try UBUNTU SERVER, and so far , it was doing good , wala pang major problem na na e-encounter. :D

So, ngayon na po, we are planning on a web cache proxy server, since our Office is frequently visiting certains sites, 

"SQUID as a proxy server", gusto kasi namin gawin set-up is TRANSPARENT para hindi na po namin configure pa yung mga users on their part to change their setting para sa proxy server, if ever po ba ganito ang set-up namin and nagka problem itong proxy namin, automatic pa rin ba na mawawalan ng internet ang mga users namin...kasi kung yung normal settings lang po ng proxy, once mag down yung proxy automatic down din ang browsing tama po ba, so yun po ang gusto namain maiwasan, maiiwasan po ba to kung se-setup namin as transparent.


Thanks in Advance

Tingin ko down din ang internet nung iba kasi router din sya.

---

### Post by pogztimz on 2009-06-03
> **zanda said:**
> Guys ask ko lang po ang opinions, experience anything you can share...

First share ko lang po ito, again, I'd like to promote UBUNTU SERVER's sa office namin :guitar:, since part ako ng I.T. administration, First Project po namin is our FTP server, before it was running on Windows, and luckily I convinced them that we try UBUNTU SERVER, and so far , it was doing good , wala pang major problem na na e-encounter. :D

So, ngayon na po, we are planning on a web cache proxy server, since our Office is frequently visiting certains sites, 

"SQUID as a proxy server", gusto kasi namin gawin set-up is TRANSPARENT para hindi na po namin configure pa yung mga users on their part to change their setting para sa proxy server, if ever po ba ganito ang set-up namin and [COLOR="Red"]nagka problem itong proxy namin, automatic pa rin ba na mawawalan ng internet ang mga users namin[/COLOR]...kasi kung yung normal settings lang po ng proxy, once mag down yung proxy automatic down din ang browsing tama po ba, [COLOR="Red"]so yun po ang gusto namain maiwasan, maiiwasan po ba to kung se-setup namin as transparent.[/COLOR]


Thanks in Advance


pwede po ba malaman kung anong klaseng problema ang ibig mong sabihin? ito ba ay hardware related or software related? or ang ibig mo bang sabihin is "kung ma down ang proxy server down din ang ftp server?

---

### Post by Ravskie on 2009-06-03
in my opinion if i understand your question correctly is you want to setup Squid transparent proxy server right... i think user will be down also if your transparent proxy is down, it because when you setup your proxy you have to configure the ip range right and also you have to point all the user to the proxy so whenever the proxy is down normally user will be down ...... ( do i make sense ...? lol )

meron po ba sa squid proxy na parang failover or redundancy ?

---

### Post by kiminaiseah on 2009-06-03
> **zanda said:**
> Guys ask ko lang po ang opinions, experience anything you can share...

First share ko lang po ito, again, I'd like to promote UBUNTU SERVER's sa office namin :guitar:, since part ako ng I.T. administration, First Project po namin is our FTP server, before it was running on Windows, and luckily I convinced them that we try UBUNTU SERVER, and so far , it was doing good , wala pang major problem na na e-encounter. :D

So, ngayon na po, we are planning on a web cache proxy server, since our Office is frequently visiting certains sites, 

"SQUID as a proxy server", gusto kasi namin gawin set-up is TRANSPARENT para hindi na po namin configure pa yung mga users on their part to change their setting para sa proxy server, if ever po ba ganito ang set-up namin and nagka problem itong proxy namin, automatic pa rin ba na mawawalan ng internet ang mga users namin...kasi kung yung normal settings lang po ng proxy, once mag down yung proxy automatic down din ang browsing tama po ba, so yun po ang gusto namain maiwasan, maiiwasan po ba to kung se-setup namin as transparent.


Thanks in Advance


add ko lang.. much simplier

squid+shorewall

#in squid.conf
acl internal_network src 192.168.1.0/24
http_access allow internal_network
http_port 192.168.1.1:3128 transparent
visible_hostname $hostname

#in shorewall's rules
DNAT eth0 eth0:192.168.1.1:3128 tcp 80
#in shorewall's masq
eth0:192.168.1.1 192.168.1.0/24 - 3128


hope you enjoy!

---

### Post by kiminaiseah on 2009-06-03
> **Ravskie said:**
> in my opinion if i understand your question correctly is you want to setup Squid transparent proxy server right... i think user will be down also if your transparent proxy is down, it because when you setup your proxy you have to configure the ip range right and also you have to point all the user to the proxy so whenever the proxy is down normally user will be down ...... ( do i make sense ...? lol )

meron po ba sa squid proxy na parang failover or redundancy ?

yup me redundancy,, but u need 3 pc to setup this on

DRBD + HA + LVADMIN

medyo complicated ang configuration kaya hirap i explain sa message

---

