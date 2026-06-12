---
title: "BIND as a caching and forwarding server"
date: 2011-10-24
forum: New to Ubuntu
---

### Post by siddharthd101 on 2011-10-24
Hi I am absolutely new to Ubuntu and Linux. I applied to an entry level job and as a part of hiring process, they have given me an assignment to do
 
They have asked me to get BIND running as a caching and forwarding DNS server with the following specific constraints:
 
•         It must forward to servers at OpenDNS and/ or  Google
•         show evidence of it resolving a public FQDN (output from DIG is preferred)
•         provide the content of any configuration files you had to edit or create
•         host a zone (provide evidence of resolving a record in the zone)




Now this is something really above me and i was not expecting something like this for a job which is not asking for any experience. I downloaded Ubuntu today and then installed bind.


I tried to find how to do it online but ended up confused. My questions are:


1. In the named.conf.local file, it asks to enter domain name in zones. What does it mean by domain name? I don't have any domain name. 



2. In named.conf.options file, in the forwarders sections, i think i have to enter the address for opendns. Right?


3. In zone definition file, what should be put for DNS server name and mail server name?




I would really really appreciate any suggestions or comments. Sorry for my ignorance regarding Ubuntu and dns. I am just trying to learn.

---

### Post by randomguy6 on 2011-11-16
Yea, I got the same challenge. My very first time with dns or Linux or ubuntu too

---

