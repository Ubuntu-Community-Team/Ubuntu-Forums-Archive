---
title: "ppp0 error while getting interface flags : no such device"
date: 2008-10-22
forum: New to Ubuntu
---

### Post by expza on 2008-10-22
Heya.

Busy setting up an internet gateway. I've currently got a connection under /etc/ppp/peers/international  : it looks like this

```
noipdefault
defaultroute
replacedefaultroute
hide-password
noauth
nopersist
plugin rp-pppoe.so eth0
unit 0
user "xxxx" #*** LEAVE THIS LINE AS IS ***
```

then under /etc/network/interfaces I have this

```
auto lo
iface io inet loopback

auto eth0
iface eth0 inet static
address 192.168.0.99
netmask 255.255.255.0

auto ppp0
iface ppp0 inet ppp
provider international

```

When I type ifup ppp0 I get :
ppp0: error while getting interface flags : no such device

I then go ifconfig ppp0 and it reports up with an IP Address and all, but if I try ping anything it's unable to resolve the host.

:confused::confused:

---

### Post by SupaSonic on 2008-10-22
Have you tried 
```
sudo pppoeconf
```
It sets PPPoE up automatically.

Then you can type 
```
pon dsl-provider
```
to turn it on, 
```
poff
``` 
to turn it off, and
```
plog
```
to get the log.

---

### Post by expza on 2008-10-22
I used pppoeconf to make two accounts, renamed the one International and the one Local. Then I edited my /interfaces to auto ppp0 with international and auto ppp1 with local. The local account is the same as the international one above but without default route, replacedefaultroute, unit 0 and I added usepeerdns.

Completely ignoring the local account tho, if I go ifup international it "connects" (with the error while getting interface flags) and if I go ifconfig ppp0 it shows an ip address, but I cant ping anything.

---

### Post by expza on 2008-10-22
p.s. what's the difference between ifup and pon ?

---

### Post by SupaSonic on 2008-10-22
> **expza said:**
> p.s. what's the difference between ifup and pon ?

pon is used specifically with PPPoE. So try pon local or pon International. You can use ifdown/ifup for your eth0 interface. That I assume will bring down PPPoE too.

Try

```

sudo ifdown eth0
sudo ifup eth0
pon Local

```

If you still aren't connected type
```
plog
```

---

### Post by expza on 2008-10-22
[IMG]http://i74.photobucket.com/albums/i266/mikemullany/DSC00231.jpg[/IMG]

As you can clearly see, I have an ip in the above ifconfig, but plog has that one error message there that raises an eyebrow "Cannot determine ethernet address for proxy arp"

p.s. ifconfig does report my ethernet having an ip address, and it can ping other computers. I did not specify any proxy when installing ubuntu nor do I use a proxy of any sorts.

---

### Post by expza on 2008-10-22
Any ideas ?

---

### Post by pabouk on 2009-02-20
> **expza said:**
> ...plog has that one error message there that raises an eyebrow "Cannot determine ethernet address for proxy arp"

That is normal if you are not using proxy arp. I have the same message with my working ppp connection.

---

