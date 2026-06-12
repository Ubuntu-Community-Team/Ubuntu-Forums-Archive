---
title: "Netflow 9 installation in Ubuntu 12.04"
date: 2014-08-18
forum: New to Ubuntu
---

### Post by deepak17 on 2014-08-18
Hi,

I need to install netflow 9 collector in my ubuntu 12.04 box.Currently I'm using the Nfsen and Nfdump in my ubuntu box.I have device enabled with netflow 9,i need to configure the same in ubuntu box and again I have issue with nfdump didn't collect any dumps.let me know how to do it?

I have install nfsen with the help of below blog
[http://blog.bravi.org/?p=1091](http://blog.bravi.org/?p=1091)

---

### Post by sandyd on 2014-08-18
> **deepak17 said:**
> Hi,

I need to install netflow 9 collector in my ubuntu 12.04 box.Currently I'm using the Nfsen and Nfdump in my ubuntu box.I have device enabled with netflow 9,i need to configure the same in ubuntu box and again I have issue with nfdump didn't collect any dumps.let me know how to do it?

I have install nfsen with the help of below blog
[http://blog.bravi.org/?p=1091](http://blog.bravi.org/?p=1091)

Do you have a netflow collector?

Try adding fprobe-ulog (requires that an IPTables rule be added) while sending to the nfdump port.

It will take a while for the data to be collected.

---

