---
title: "NetworkManager, pdnsd and FF"
date: 2012-06-18
forum: New to Ubuntu
---

### Post by tempore on 2012-06-18
I have set up pdnsd and it appears to be working.

```

c@c:~$ dig ubuntuforums.org

; <<>> DiG 9.8.1-P1 <<>> ubuntuforums.org
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 29197
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 3, ADDITIONAL: 1

;; QUESTION SECTION:
;ubuntuforums.org.        IN    A

;; ANSWER SECTION:
ubuntuforums.org.    432000    IN    A    91.189.94.12

;; AUTHORITY SECTION:
ubuntuforums.org.    432000    IN    NS    ns3.canonical.com.
ubuntuforums.org.    432000    IN    NS    ns2.canonical.com.
ubuntuforums.org.    432000    IN    NS    ns1.canonical.com.

;; ADDITIONAL SECTION:
ns1.canonical.com.    432000    IN    A    91.189.94.173

;; Query time: 114 msec
;; SERVER: 127.0.0.2#53(127.0.0.2)
;; WHEN: Mon Jun 18 22:07:04 2012
;; MSG SIZE  rcvd: 133

c@c:~$ dig ubuntuforums.org

; <<>> DiG 9.8.1-P1 <<>> ubuntuforums.org
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 13236
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 3, ADDITIONAL: 1

;; QUESTION SECTION:
;ubuntuforums.org.        IN    A

;; ANSWER SECTION:
ubuntuforums.org.    431998    IN    A    91.189.94.12

;; AUTHORITY SECTION:
ubuntuforums.org.    431998    IN    NS    ns3.canonical.com.
ubuntuforums.org.    431998    IN    NS    ns2.canonical.com.
ubuntuforums.org.    431998    IN    NS    ns1.canonical.com.

;; ADDITIONAL SECTION:
ns1.canonical.com.    431998    IN    A    91.189.94.173

;; Query time: 1 msec
;; SERVER: 127.0.0.2#53(127.0.0.2)
;; WHEN: Mon Jun 18 22:07:06 2012
;; MSG SIZE  rcvd: 133

c@c:~$ 

```

However if I clear the cache, open FireFox, type ubuntuforums.org in the address bar then do # dig ubuntuforums.org, it has no entry in pdnsd.

I think FireFox is not using pdnsd for lookups. I tried adding```
dns=pdnsd
``` in NetworkManager.conf but no changes.

Any suggestions?

---

### Post by tempore on 2012-06-19
bump

---

