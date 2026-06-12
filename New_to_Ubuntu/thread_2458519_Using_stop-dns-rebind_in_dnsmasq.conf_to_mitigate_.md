---
title: "Using stop-dns-rebind in dnsmasq.conf to mitigate DNS rebind attack"
date: 2021-02-26
forum: New to Ubuntu
---

### Post by indhujaavs on 2021-02-26
Hello,

In a "DNS Rebind Attack", the attacker controls a domain name (say attacker.com) and the corresponding DNS server with very short time-to-live (TTL). Consider a scenario where the victim accidentally browses and downloads content from a malicious domain name. The "stop-dns-rebind" flag prevents malicious javascript(from the malicious domain) to probe local network devices because dnsmasq refuses to bind the domain name to a local IP address. 

curl -v [http://10.10.10.1/](http://10.10.10.1/) --> this should return '200 OK'
curl -v [http://domainname](http://domainname) --> this should return '400 Bad request', where domain name falls under private IP address range

In both the cases, the output was 200 OK. The above is tested by enabling stop-dns-rebind flag in dnsmasq.conf and also with options (like dnsmasq -u nobody -q --clear-on-reload --bind-dynamic --stop-dns-rebind). Could someone please let me know anything else to be done to avoid DNS rebind attack.

---

