---
title: "Dual Internet Connections"
date: 2008-06-11
forum: New to Ubuntu
---

### Post by benauld345 on 2008-06-11
Hi,

I don't know if this is possible or not, is it possible to have two internet connections shared across our network via our server? Basically if I had two Draytek 110 ADSL2+ modems on two nics in my server can it be conveniently natted and what have you?

Sorry about my ignorance on the subject!! Any suggestions would be appreciated.

Ben

---

### Post by Cypher on 2008-06-11
You would need to employ Channel Bonding to basically couple the two connections to increase thruput/bandwidth..

Some reading:
[http://en.wikipedia.org/wiki/Channel_bonding](http://en.wikipedia.org/wiki/Channel_bonding)
[http://www.debianhelp.co.uk/bonding.htm](http://www.debianhelp.co.uk/bonding.htm)

---

