---
title: "unable to install docker in ubuntu 16.04"
date: 2018-10-11
forum: New to Ubuntu
---

### Post by pratap31 on 2018-10-11
Hi Team,

I'm unable to install docker 
```
sudo apt-get install docker-ceor update
sudo apt-get update

Error:
http:// security.ubuntu.com/ubuntu.com xenial-security InRelease
Temparary failur resolving 'security.ubuntu.com'
```

I have used command for changes in config and interface

```
sudo nano /etc/resolv.conf
initially it has only /* nameserver 8.8.8.8

added to the above /* nameserver 8.8.4.4
```
but it is overwritten as actuals

```
sudo nano/etc/network/interfaces

source /etc/network/interfaces.d/*

auto lo
iface lo inet loopback

allow-hotplug eth0
auto eth0
iface eth0 inet static
address my address ip
netmask my netmask
gateway my gateway
dns-nameservers 8.8.8.8 8.8.4.4

```
nothing sorted out.

Could you please let me know how to sort out this issue?

Thanks in Advance

---

### Post by wildmanne39 on 2018-10-11
Hello and welcome to the forum!

*Thread moved to **New to Ubuntu for a more appropriate fit**.*

Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by deadflowr on 2018-10-11
Post the output for
```
sudo apt-get update
```
and the output for the sources.list file that it needs to read
```
cat /etc/apt/sources.list
```

---

