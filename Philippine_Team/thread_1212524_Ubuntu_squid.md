---
title: "Ubuntu squid"
date: 2009-07-13
forum: Philippine Team
---

### Post by Myronray on 2009-07-13
mga kabayan sino sa inyo familiar sa transparent proxy using squid?

thanks

---

### Post by loell on 2009-07-14
dude, ano palang problema sa setup natin? :)

---

### Post by Myronray on 2009-07-14
hi sir gud evening

im planning to put squid transparent proxy i have my Mikrotik 5 port router and gusto ko lang po malaman kung pano mag add sa parameter dun sa squid.conf kung anong address dun ilagay ko kaka setup ko lang ng latest release ng ubuntu server ito po setup ko sa router ko at anytime pd ko e config redirect sa proxy

ether1 = wan >> ISP
ether2 = application server OPERA MICROS 10.2.2.1/24
ether3 = office network 10.11.0.1/24
ether4 = hotel hotspot 10.12.0.1/24
ether5 = transparent proxy 10.13.0.2

kung andun na ako sa squid.conf ano po e modify ko dun sir
na yung ether 2, 3, and 4 redirect sa ether5 which is yung proxy ko san ko e modify banda dito sir?

#Recommended minimum configuration:
acl all src all
acl manager proto cache_object
acl localhost src 127.0.0.1/32
acl to_localhost dst 127.0.0.0/8
#
# Example rule allowing access from your local networks.
# Adapt to list your (internal) IP networks from where browsing
# should be allowed
acl localnet src 10.0.0.0/8     # RFC1918 possible internal network
acl localnet src 172.16.0.0/12  # RFC1918 possible internal network
acl localnet src 192.168.0.0/16 # RFC1918 possible internal network
#
acl SSL_ports port 443          # https
acl SSL_ports port 563          # snews
acl SSL_ports port 873          # rsync
acl Safe_ports port 80          # http
acl Safe_ports port 21          # ftp
acl Safe_ports port 443         # https
acl Safe_ports port 70          # gopher
acl Safe_ports port 210         # wais
acl Safe_ports port 1025-65535  # unregistered ports
acl Safe_ports port 280         # http-mgmt
acl Safe_ports port 488         # gss-http
acl Safe_ports port 591         # filemaker
acl Safe_ports port 777         # multiling http
acl Safe_ports port 631         # cups
acl Safe_ports port 873         # rsync
acl Safe_ports port 901         # SWAT
acl purge method PURGE

thanks and most appreciated sir

---

### Post by Myronray on 2009-07-14
any help?

thanks

---

### Post by loell on 2009-07-15
I believe you will just have to add, these three items.


acl internal_network src 10.2.2.1/24

acl internal_network src 10.11.0.1/24

acl internal_network src 10.12.0.1/24

---

### Post by Myronray on 2009-07-15
ok sir loell i try this now if works

how about this one bro >>> acl all src all? should be acl all src all 0.0.0.0/0.0.0.0?

salamat bro

---

### Post by Myronray on 2009-07-15
still no luck :)

---

### Post by loell on 2009-07-15
maybe it should be **acl localnet src ** instead.

can you also attach your conf, for others to see as well.

---

### Post by Myronray on 2009-07-15
#Recommended minimum configuration:
acl all src 0.0.0.0/0.0.0.0
acl manager proto cache_object
acl localhost src 127.0.0.1/32
acl to_localhost dst 127.0.0.0/8
#
# Example rule allowing access from your local networks.
# Adapt to list your (internal) IP networks from where browsing
# should be allowed
acl localnet src 10.2.2.0/24  # RFC1918 possible internal network
acl localnet src 10.11.0.0/24 # RFC1918 possible internal network
acl localnet src 10.12.0.0/24 # RFC1918 possible internal network
#
acl SSL_ports port 443          # https
acl SSL_ports port 563          # snews
acl SSL_ports port 873          # rsync
acl Safe_ports port 80          # http
acl Safe_ports port 21          # ftp
acl Safe_ports port 443         # https
acl Safe_ports port 70          # gopher
acl Safe_ports port 210         # wais
acl Safe_ports port 1025-65535  # unregistered ports
acl Safe_ports port 280         # http-mgmt
acl Safe_ports port 488         # gss-http
acl Safe_ports port 591         # filemaker
acl Safe_ports port 777         # multiling http

i test my router to redirect its sending packets but the squid no hits

MIKROTIK router

transparent squid
     chain=dstnat action=redirect to-ports=3128 protocol=tcp dst-port=80 

myron@MikroTik] /ip> proxy print
                 enabled: yes
             src-address: 0.0.0.0
                    port: 3128
            parent-proxy: 0.0.0.0
       parent-proxy-port: 0
     cache-administrator: "webmaster"
          max-cache-size: none
           cache-on-disk: no
  max-client-connections: 600
  max-server-connections: 600
          max-fresh-time: 3d
   serialize-connections: no
       always-from-cache: no
          cache-hit-dscp: 4
             cache-drive: system

i suspected in the squid config baka meron pa gagalwin sa incoming port at ip source
baka meron ka idea sir loell now lang ako naka try mag setup ng transparent proxy

thanks sir

---

### Post by loell on 2009-07-15
yeah well, it also involves routing the traffic to the squid proxy.

---

### Post by Myronray on 2009-07-15
ok thanks anyway i try my best to up this machine

salamat

---

