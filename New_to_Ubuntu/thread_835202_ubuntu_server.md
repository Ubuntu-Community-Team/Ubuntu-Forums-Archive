---
title: "ubuntu server"
date: 2008-06-20
forum: New to Ubuntu
---

### Post by ub007 on 2008-06-20
hi,

i just installed a dhcp server and configured the /etc/dhcpd.conf file.

default-lease-time 600;
max-lease-time 7200;
option subnet-mask 255.255.255.0;
option broadcast-address 192.168.1.255;
option routers 192.168.1.254;

subnet 192.168.1.0 netmask 255.255.255.0 {
range 192.168.1.10 192.168.1.100;
range 192.168.1.150 192.168.1.200;
} 

its a stand alone server and havent connected any clients to it.How do i test whether the configuration works fine?

cheers,
David

---

### Post by hyper_ch on 2008-06-20
restart the dhcp server and then read the syslog (or dhcp log if there is a specific one) and see if there are error messages :)

---

