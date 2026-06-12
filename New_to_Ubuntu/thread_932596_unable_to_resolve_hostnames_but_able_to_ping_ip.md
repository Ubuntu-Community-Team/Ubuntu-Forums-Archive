---
title: "unable to resolve hostnames but able to ping ip"
date: 2008-09-28
forum: New to Ubuntu
---

### Post by oldelfy on 2008-09-28
Until recently (last 12 hours) I was happily able to access the ouside world from within one of my vms, but recently I've stopped being able to resolve hostnames from within the server, I can ping external IPs no problem and traceroute them, but I can no longer ping google.co.uk for example. The websites hosted within the server seem to be working fine and can be accessed from outside the VM no problem. I've changed the dns-nameservers but it doesn't seem to make a difference.
# dns-* options are implemented by the resolvconf package, if installed
	dns-nameservers 4.2.2.2 217.112.88.90 217.112.87.147

I can dig fine like this
dig google.co.uk @217.112.87.147

; <<>> DiG 9.4.2-P1 <<>> google.co.uk @217.112.87.147
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 30842
;; flags: qr rd ra; QUERY: 1, ANSWER: 3, AUTHORITY: 0, ADDITIONAL: 0

but if i just do this
dig google.co.uk

; <<>> DiG 9.4.2-P1 <<>> google.co.uk
;; global options:  printcmd
;; connection timed out; no servers could be reached

nothign :(

---

### Post by victorbrca on 2008-09-28
just out of curiosity, what does your resolv.conf says?


Vic.

---

