---
title: "Ubuntu Server DNS Status:SERVFAIL"
date: 2011-10-28
forum: New to Ubuntu
---

### Post by cris@smp.com.ph on 2011-10-28
:confused: Can someone lighten me up why my DNS Ubuntu Server giving me a Result Failed for DNS
This was far i can configure and still giving me the status of a SERVFAIL

```
root@ubuntu-server:/etc/bind# vi db.ubuntu-server.ph
;
; BIND data file for ubuntu-server.ph
;
$TTL    1d
@       IN      SOA     ns1.ubuntu-server.ph root.ubuntu-server.ph. (
                              2         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
@       IN      NS      ns1.ubuntu-server.ph
@       IN      A       192.168.0.30
NS1     IN      A       192.168.0.30
www     IN      A       192.168.0.30
gateway IN      A       192.168.0.3

``````
root@ubuntu-server:/etc/bind# vi named.conf
// This is the primary configuration file for the BIND DNS server named.
//
// Please read /usr/share/doc/bind9/README.Debian.gz for information on the
// structure of BIND configuration files in Debian, *BEFORE* you customize
// this configuration file.
//
// If you are just adding zones, please do that in /etc/bind/named.conf.local

include "/etc/bind/named.conf.options";
include "/etc/bind/named.conf.local";
include "/etc/bind/named.conf.default-zones";

``````
root@ubuntu-server:/etc/bind# vi named.conf.local
//
// Do any local configuration here
//

// Consider adding the 1918 zones here, if they are not used in your
// organization
include "/etc/bind/zones.rfc1918";

``````
root@ubuntu-server:/etc/bind# vi zones.rfc1918
zone "ubuntu-server.ph"     { type master; file "/etc/bind/db.ubuntu-server.ph";};

```BUT STILL GIVING ME THIS RESULT WHERE I WENT WORNG?

```
root@ubuntu-server:/etc/bind# nslookup ubuntu-server.ph
Server:         192.168.0.30
Address:        192.168.0.30#53

** server can't find ubuntu-server.ph.ubuntu-server.ph: SERVFAIL

```AND ALSO IN DIG COMMAND Status:SERVFAIL

```
root@ubuntu-server:/etc/bind# dig ubuntu-server.ph

; <<>> DiG 9.7.3 <<>> ubuntu-server.ph
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: SERVFAIL, id: 64328
;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;ubuntu-server.ph.              IN      A

;; Query time: 0 msec
;; SERVER: 192.168.0.30#53(192.168.0.30)
;; WHEN: Fri Oct 28 14:33:56 2011
;; MSG SIZE  rcvd: 34

```can some one help me?

---

### Post by veggis on 2011-10-28
try to remove ns1. db.ubuntu-server.ph and add the name of the server to nameonserver IN A 192.168.0.30

```
root@ubuntu-server:/etc/bind# vi db.ubuntu-server.ph
;
; BIND data file for ubuntu-server.ph
;
$TTL    1d
@    IN    SOA     ubuntu-server.ph root.ubuntu-server.ph. (
                              2               ; Serial
                         604800         ; Refresh
                          86400          ; Retry
                        2419200        ; Expire
                         604800 )       ; Negative Cache TTL
;
@    IN    NS    ubuntu-server.ph
@    IN    A    192.168.0.30
NS1     IN    A    192.168.0.30
www     IN    A    192.168.0.30
gateway IN    A    192.168.0.3

```

---

