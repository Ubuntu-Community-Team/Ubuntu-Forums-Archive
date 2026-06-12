---
title: "Dnssec dnsmasq"
date: 2023-03-27
forum: New to Ubuntu
---

### Post by jjbach on 2023-03-27
Are these features built into Ubuntu?
DNSSEC DNSMASQ

---

### Post by grahammechanical on 2023-03-27
I am not an expert on any of this but here is what I found on DNSMASQ:

[https://wiki.archlinux.org/title/dnsmasq](https://wiki.archlinux.org/title/dnsmasq)

I run to command to see if dnsmasq had started properly. This is on Ubuntu 20.04 desktop. This is the result I get:

> ~$ journalctl -u dnsmasq.service
-- Logs begin at Tue 2022-05-24 12:12:17 BST, end at Mon 2023-03-27 18:31:01 BS>
-- No entries --

I did not do anything to install dnsmasq. So, the answer in this case must be, yes.

As regards DNSSEC I found something  about opendnssec.

[https://manpages.ubuntu.com/manpages/bionic/man7/opendnssec.7.html](https://manpages.ubuntu.com/manpages/bionic/man7/opendnssec.7.html)

I do not know if opendnssec is in Ubuntu desktop or Ubuntu server. In my ignorance, I am of the opinion that opendnssec is a protocol and its application is appropriate regarding and program being used as a DNS server. I have no knowledge of which programs can be used as DNS servers.

This link discusses how to install a DNS server called bind9.

[https://linuxhint.com/configure-dns-server-ubuntu/](https://linuxhint.com/configure-dns-server-ubuntu/)

So, I guess that the answer in regards to DNSMASQ is no but it may be part of bind9 which can be installed in Ubuntu.

Regards

---

### Post by MAFoElffen on 2023-03-30
No.

Not installed by default. After 18.04, which uses systemd-resolved, when you do install dnsmasq you have to disable and turn that service off... Then remove the symlink at /etc/resolv.conf, to be able to create a manual resolv.conf file... So that you can get DNS to be able to install it.

'dnsmasq' is it's own package. If you want to enable DNSSEC validation and caching, you uncomment a line for that within /etc/dnsmasq.conf.

Bind9 is a different, full blown, DNS Service package.

Good tutorial: [https://computingforgeeks.com/install-and-configure-dnsmasq-on-ubuntu/](https://computingforgeeks.com/install-and-configure-dnsmasq-on-ubuntu/)

---

