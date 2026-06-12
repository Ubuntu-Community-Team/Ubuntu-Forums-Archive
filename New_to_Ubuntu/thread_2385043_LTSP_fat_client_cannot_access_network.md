---
title: "LTSP fat client cannot access network"
date: 2018-02-15
forum: New to Ubuntu
---

### Post by stlord on 2018-02-15
Greetings.

I built LTSP-standalone server with tftpd-hpa and isc-dchp included. Everything went ok, but when I got my client started, I found, it can't access network.
It getting IP from dhcp server, netmask and no more. No default gw, no ping gw ip, though gw is in the same network. Pinging LTSP server is ok.
When i'm going to "Edit connections" on client, I see no connections at all, but I can create one and assign the only physical NIC there (nothing changes at all).

What did I do wrong?

dhcpd.conf:
```
subnet 192.168.88.0 netmask 255.255.255.0 {
    range 192.168.88.20 192.168.88.120;
    option domain-name-servers 8.8.8.8;
    option broadcast-address 192.168.88.255;
    option routers 192.168.88.1;
    next-server 192.168.88.201;
    option subnet-mask 255.255.255.0;
    option root-path "/opt/ltsp/amd64";
    if substring( option vendor-class-identifier, 0, 9 ) = "PXEClient" {
        filename "/ltsp/amd64/pxelinux.0";
    } else {
        filename "/ltsp/amd64/nbi.img";
    }
}

```

Can't show ifconfig from client, but there's no something weird.

---

### Post by Tadaen_Sylvermane on 2018-02-15
This is mine.

```
## Default LTSP dhcpd.conf config file.
#


authoritative;


subnet 192.168.1.0 netmask 255.255.255.0 {
    range 192.168.1.150 192.168.1.250;
    option domain-name-servers 192.168.1.2, 192.168.1.3, 192.168.1.4;
    option broadcast-address 192.168.1.255;
    option routers 192.168.1.1;
    next-server 192.168.1.2;
    option subnet-mask 255.255.255.0;
    option root-path "/opt/ltsp/desktop";
    if substring( option vendor-class-identifier, 0, 9 ) = "PXEClient" {
        filename "/ltsp/desktop/pxelinux.0";
    } else {
        filename "/ltsp/desktop/nbi.img";
    }
}

```

Are you posting your entire dhcpd.conf or just a clip. If so that is the problem. You are missing the authoritative; part.

Also is this the dhcpd.conf in the /etc/ltsp  folder? If so did you include it in the main config file?

```
include "/etc/ltsp/dhcpd.conf";
```

in /etc/dhcp/dhcpd.conf?

*EDIT* Another thing, did you make sure to disable the dhcp server on the router and let this server take control of dhcp. Won't work right if you don't do that.

---

