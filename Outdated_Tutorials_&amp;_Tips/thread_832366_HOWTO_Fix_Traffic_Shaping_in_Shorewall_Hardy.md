---
title: "HOWTO: Fix Traffic Shaping in Shorewall Hardy"
date: 2008-06-17
forum: Outdated Tutorials &amp; Tips
---

### Post by sherl0ck on 2008-06-17
Summary: Traffic Shaping in Shorewall 4.0.6 in Hardy breaks on compile and wondershaper will fail. To fix you need to replace iproute. 

**_ERROR:_**
> 
Setting up Traffic Control...
What is "flowid"?
Illegal "police"
   ERROR: Command "tc filter add dev eth0 parent ffff: protocol ip prio 50 u32 match ip src 0.0.0.0/0 police rate 500kbps burst 10k drop flowid :1" Failed
[U][B]
FIX:[/B][/U]

Enter root:
```
sudo -i
```
Install tools:
```
apt-get install build-essential fakeroot devscripts 
```
Make a working directory:
```
mkdir /tmp/iproutefix && cd /tmp/iproutefix 
```
Download DebDiff:
```
wget  http://launchpadlibrarian.net/15355596/iproute_20071016-2ubuntu2.debdiff
```
Get the package source tree:
```
apt-get source iproute
```
Install libraries needed to build the source package:
```
apt-get build-dep -y iproute
```
Apply the debdiff changes:
```
cd iproute-* && patch -p1 < ../ iproute_20071016-2ubuntu2.debdiff
```
Build the new source package:
```
debuild -uc -us 
```
Install the resulting binary package:
```
dpkg -i ../iproute*.deb 
```
ALL DONE!


_**REFERENCES:**_
[Bug #194623]("https://bugs.launchpad.net/ubuntu/+source/shorewall/+bug/194623")
[DebDiff Wiki]("https://wiki.ubuntu.com/UbuntuPackagingGuide/BuildFromDebdiff?highlight=(debdiff)")

---

