---
title: "Ubuntu 14.04 DNS configuration"
date: 2014-12-09
forum: New to Ubuntu
---

### Post by sashi4 on 2014-12-09
Hi everyone,

I am given a task to configure a pair of DNS servers, (ns1) & (ns2).  ns1 will be sitting at the data center & ns2 will be sitting in my  office. Both of these machines will running mail services, (mx1) &  (m2).

ns1 - 210.x.x.x (master)
mx1 - 210.x.x.x (backup mx with priority set as 20)

ns2 - 122.y.y.y (slave)
mx2 - 122.y.y.y (primaxy mx with priority set as 10)

My doubts are is that, is it even possible to configure DNS forward  & reverse zone files with IP address of different range? Somehow  rather, i have created both the forward & reverse zone files for  ns1, can someone please guide me in the correct dirrection?


Forward Zone
```

$TTL    604800
@       IN      SOA     ns1.example.com. hostmaster.example.com. (
                              2         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
        IN      A       210.x.x.x
        IN      A       122.y.y.y
;
;Primary nameserver
@       IN      NS      ns1.example.com.
@       IN      A       210.x.x.x
@       IN      AAAA    ::1
ns1     IN     A       210.x.x.x
;Secondary nameserver
@       IN      NS      ns2.example.com.
@       IN      A       122.y.y.y
@       IN      AAAA    ::1
ns2     IN     A       122.y.y.y
;Primary MX
        IN      MX 20   mx1.x.x.x.
mx1     IN      A       210.x.x.x
;Secondary MX
        IN      MX 10   mx2.y.y.y.
;Common records
mx2     IN      A       122.y.y.y
localhost       IN      A       127.0.0.1
webmail         CNAME   mx2
smtp            CNAME   mx2
imap            CNAME   mx2
pop3            CNAME   mx2
webmail2        CNAME   mx2
www             CNAME   ns1
ftp             CNAME   ns1

```

Reverse Zone
```

$TTL    604800
@       IN      SOA     ns1.example.com. hostmaster.example.com. (
                              2         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
@       IN      NS      ns1.
143     IN      PTR     ns1.example.com.
@       IN      NS      ns2.
149     IN      PTR     ns2.example.com.
;
149     IN      PTR     webmail.example.com.
149     IN      PTR     smtp.example.com.
149     IN      PTR     imap.example.com.
149     IN      PTR     pop3.example.com.
149     IN      PTR     webmail2.example.com.
143     IN      PTR     www.example.com.
143     IN      PTR     ftp.example.com.

```

Can someone please help me to check if these zone files are properly configured? Thank you.

---

### Post by lisati on 2014-12-09
Please do not start multiple threads for the same problem, it dilutes the community's ability to help.

Duplicate of [http://ubuntuforums.org/showthread.php?t=2255974](http://ubuntuforums.org/showthread.php?t=2255974) closed.

---

