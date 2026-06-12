---
title: "Postfix problem"
date: 2012-10-21
forum: New to Ubuntu
---

### Post by Shinonuma on 2012-10-21
Hi,

I'm trying to set up postfix. I followed this tutorial: [https://help.ubuntu.com/community/PostfixBasicSetupHowto](https://help.ubuntu.com/community/PostfixBasicSetupHowto)

I did everything and it all works untill the " Adding your local domains to postfix " 

When I use localhost it works fine:

```
test@test-VirtualBox:~$ netcat localhost 25
220 test-VirtualBox ESMTP Postfix (Ubuntu)
```

but if I try netcat mail.lintest.be 25 it says

```
netcat: getaddrinfo: Name or service not known
```

This is mydestination:

```
mydestination = mail-linux, test-VirtualBox, localhost.localdomain, localhost, lintest.be
```

and mynetworks:

```
mynetworks = 127.0.0.0/8, 192.168.56.0/24
```

The rest is the same as the tutorial above.

```
test@test-VirtualBox:~$ telnet localhost 25
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
220 test-VirtualBox ESMTP Postfix (Ubuntu)
```


```
test@test-VirtualBox:~$ telnet mail.lintest.be 25
telnet: could not resolve mail.lintest.be/25: Name or service not known
```

Some other files:


 /etc/network/interfaces file:
```

auto eth0
iface eth0 inet static
address 192.168.56.20
netmask 255.255.255.0
network	192.168.56.0
broadcast 192.168.56.255
gateway 192.168.56.1
auto lo
iface lo inet loopback
```

 /etc/resolvconf/resolv.conf.d/base 

```
nameserver 192.168.56.20
nameserver 192.168.56.10
```

 /etc/bind/named.conf.local 

```
//
// Do any local configuration here
//

// Consider adding the 1918 zones here, if they are not used in your
// organization
//include "/etc/bind/zones.rfc1918";

zone "lintest.be"{
        type master;
        file "/etc/bind/zones/lintest.be.db";
}

```
 /etc/bind/named.conf.options 

```
options {
        directory "/var/cache/bind";

        // If there is a firewall between you and nameservers you want
        // to talk to, you may need to fix the firewall to allow multiple
        // ports to talk.  See http://www.kb.cert.org/vuls/id/800113

        // If your ISP provided one or more IP addresses for stable
        // nameservers, you probably want to use them as forwarders.
        // Uncomment the following block, and insert the addresses replacing
        // the all-0's placeholder.

recursion yes;

        forwarders {
                192.168.56.10;
        };

        auth-nxdomain no;    # conform to RFC1035
        listen-on-v6 { any; };
};

```

 /etc/bind/zones/lintest.be.db


```

$TTL 3D
@ IN SOA ns.mydomain.be. admin.mydomain.be. (
   2007062002
   28800
   3600
   604800
   38400
);
lintest.be.  IN      NS         ns.lintest.be.
mail.lintest.be.        IN      MX      10      www.lintest.be.
www             IN      A       192.168.56.10
ns.lintest.be.  IN      A       192.168.56.20


```

Does anybody know the problem?

Thanks in advance

---

### Post by Doug S on 2012-10-23
I don't think your problem is a postfix problem. I think one problem, there may be others, is bind configuration. Suggest this for db.lintest.be:```
;
; BIND data file for internal only, lintest.be
;
$TTL 3D
@ IN SOA lintest.be. admin.lintest.be. (
   2012102201           ;Serial
   28800                ;Refresh
   3600                 ;Retry
   604800               ;Expire
   38400 )              ;Negative Cash TTL
        IN      A       192.168.56.20
;
@       IN      NS      ns.lintest.be.
        IN      MX 10   mail.lintest.be.
ns      IN      A       192.168.56.20
www     IN      A       192.168.56.10
mail    IN      A       192.168.56.10

```You might also need mail.lintest.be in "mydestination", but I'm not sure.
Hope this helps.

---

