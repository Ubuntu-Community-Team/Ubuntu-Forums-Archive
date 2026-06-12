---
title: "Ubuntu 8.04 LTS: Dynamic DHCP and Chroot Bind9 DNS Server"
date: 2009-10-06
forum: Outdated Tutorials &amp; Tips
---

### Post by nyu2007 on 2009-10-06
Dear all,

The test system in on VMWare 2.0

[B]Ubuntu 8.04 LTS Server
IP: 192.168.100.2
Hostname: bdc-svr.example.com
[/B]

- Enable the root account
```
sudo passwd
su
```

- Edit file /etc/hosts
```
...
127.0.0.1          localhost
192.168.100.2   bdc-svr.example.com    bdc-svr
...
```

- Edit file /etc/network/interfaces
```
...
auto eth0
iface eth0 inet static
    address 192.168.100.2
    netmask 255.255.255.0
    gateway 192.168.100.254 # Gateway to lookup outside
...
```

- Restart network
```
/etc/init.d/networking restart
```
or
```
/etc/init.d/hostname.sh start
```

- Test run
```
hostname ----> bdc-svr
hostname -f -----> bdc-svr.example.com
hostname -d -----> example.com
```

- Update and Upgrade System

```
apt-get update
apt-get upgrade
```

This step is very important. I look around to solved it
- Disable AppArmor
```
/etc/init.d/apparmor stop
update-rc.d -f apparmor remove
```

- Optional
```
apt-get install ntp
apt-get install ssh openssh-server
apt-get install tree
```

**- Reboot**

apt-get install dhcp3-server bind9
```
/etc/init.d/dhcp3-server stop
/etc/init.d/bind9 stop
```


**1. Configuration DHCP Server**
- Tell the DHCP server to only run on eth0 need edit file /etc/default/dhcp3-server
```
nano /etc/default/dhcp3-server

INTERFACES="eth0"
```

- There are 2 zones map hostnames and reverse lookups
- example.com: zone that will map hostnames to IP address.
- 100.168.192.in-addr.arpa: zone in change of reverse lookups

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
DHCPD.CONF
```
ddns-update-style interim;
include "/etc/bind/rndc.key";

zone example.com. {
    primary 127.0.0.1;
    key "rndc-key";
}

ddns-domainname "example.com";
option domain-name "example.com";
option domain-name-servers 192.168.100.2;
option routers 192.168.100.254;
option broadcast-address 192.168.100.255;


default-lease-time 600;
max-lease-time 7200;

authoritative;

log-facility local7;

subnet 192.168.100.0 netmask 255.255.255.0 {
    range 192.168.100.1 192.168.100.10;
   
    zone example.com. {
        primary 192.168.100.2;
        key "rndc-key";
    }

    zone 100.168.192.in-addr.arpa. {
        primary 192.168.100.2;
        key "rndc-key";
    }
}
```
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

**2. Configuration Bind9**
- Make sure the file /etc/bind/named.conf contains the following

```
include "/etc/bind/named.conf.local";
include "/etc/bind/named.conf.options";
```

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
NAMED.CONF.OPTIONS
```
options {
    directory "/var/cache/bind";

    // If there is a firewall between you and nameservers you want
    // to talk to, you might need to uncomment the query-source
    // directive below.  Previous versions of BIND always asked
    // questions using port 53, but BIND 8.1 and later use an unprivileged
    // port by default.

    query-source address * ;

    // If your ISP provided one or more IP addresses for stable
    // nameservers, you probably want to use them as forwarders. 
    // Uncomment the following block, and insert the addresses replacing
    // the all-0's placeholder.

    forwarders {
        208.67.222.222;
    };
   
    recursion yes;
    version "REFUSED";

    allow-recursion {
        127.0.0.1;
        192.168.100.0/24;
    };

    allow-query {
        127.0.0.1;
        192.168.100.0/24;
    };


    auth-nxdomain no;    # conform to RFC1035
    listen-on-v6 { any; };
};
```
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
NAMED.CONF.LOCAL
```
//
// Do any local configuration here
//

// Consider adding the 1918 zones here, if they are not used in your
// organization
//include "/etc/bind/zones.rfc1918";

include "/etc/bind/rndc.key";

controls {
    inet 127.0.0.1 allow { localhost; } keys { "rndc-key"; };
};

zone "100.168.192.in-addr.arpa" {
    type master;
    notify no;
    file "db.100.168.192";
    allow-update { key "rndc-key"; };
};

zone "example.com" {
    type master;
    file "db.example.com";
    allow-update { key "rndc-key"; };
};

zone "static.example.com" {
   type master;
   file "db.static";
};
```
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

**3. Configure DNS Zones**
- example.com: file /var/cache/bind/db.exaple.com: dynamic zone, updated by DHCP when a computer gets an IP from it.
- 100.168.192: file /var/cache/bind/: dynamic zone, will contain information about machines using DHCP

/var/cache/bind/db.example.com
```
$TTL 86400;
@            IN       SOA      bdc-svr.example.com.    admin.example.com. (
    20090929    ; Serial
       28800    ; Refresh ( 8 hours)
        7200    ; Retry ( 2 hours)
     2419200    ; Expire ( 4 weeks)
      86400     ; Minimum ( 1 day)
)
example.com.    IN    NS    bdc-svr.example.com.
example.com.    IN    MX    10    mail-svr.example.com.
bdc-svr         IN    A    192.168.100.2
pdc-svr         IN    A    192.168.100.1
mail-svr        IN    A    192.168.100.3
```


/var/cache/bind/db.100.168.192
```
$TTL 86400;
@          IN       SOA    bdc-svr.example.com.    admin.example.com. (
    20090929    ; Serial
       28800    ; Refresh ( 8 hours)
        7200    ; Retry ( 2 hours)
     2419200    ; Expire ( 4 weeks)
      86400     ; Minimum ( 1 day)
)
          IN    NS      bdc-svr.example.com.
1         IN    PTR    pdc-svr.example.com.
2         IN    PTR    bdc-svr.example.com.
3         IN    PTR    mail-svr.example.com.
```


- Make sure the zones will be writable by the user "bind" and restart the services
```
chown bind. /var/cache/bind/*

**[COLOR="Red"]chmod 644 /etc/bind/rndc.key[/COLOR]** <---- 

/etc/init.d/bind9 restart
/etc/init.d/dhcp3-server restart
```

**4. Chrooted Bind**
```
/etc/init.d/bind stop
```

- Edit the file /etc/default/bind9. Modify the line: OPTIONS="-u bind" so that it reads OPTIONS="-u bind -t /var/lib/named"
- Create the necessary directories under /var/lib:

```
mkdir -v -p /var/lib/named/{etc,dev,var/{cache/bind,run/bind/run}}
mkdir /etc/bind/zones
```

- Move the config directory from /etc/bind to /var/lib/named/etc/bind

```
mv /etc/bind /var/lib/named/etc
```

- Create a symlink to the new config directory from the old location (to avoid proplems when bind gets updated in the future)

```
ln -s /var/lib/named/etc/bind /etc/bind
```

- Make null and random devices, and fix permissions of the directories:

```
mknod /var/lib/named/dev/null c 1 3
mknod /var/lib/named/dev/random c 1 8
chmod 666 /var/lib/named/dev/null /var/lib/named/dev/random
chown -R bind:bind /var/lib/named/var/*
chown -R bind:bind /var/lib/named/etc/bind
```

- Modify /etc/default/syslogd

```
nano /etc/default/syslogd
SYSLOGD="-a /var/lib/named/dev/log"
```

- Restart services daemon

```
/etc/init.d/sysklog restart
```

- Copy zones file from /var/cache/bind to /etc/bind/zones

```
cp /var/cache/bind/*  /etc/bind/zones
chown -R bind:bind /etc/bind/zones/*
```

- Edit file /etc/bind/named.conf.options
```
directory "/var/cache/bind" ----> directory "/etc/bind/zones"
```

**REBOOT SERVER**

---

