---
title: "Awk question"
date: 2011-11-01
forum: New to Ubuntu
---

### Post by Hargeet on 2011-11-01
Using awk utility, calculate total amount of failures and warnings showing in the result only count and error reason (e.g: 4  Can't connect to server. Nslookup failed)

[2011.10.14 05:45:28.169] <1260121> WARNING: timeout: outdated
[2011.10.14 05:48:38.411] <3575323> WARNING: user checking failed : State DISCONNECTED
[2011.10.14 07:30:28.332] <1264500> WARNING: rd:7 qu:0 qm:0 qc:0 qd:0modcount timeout: outdated
[2011.10.14 15:05:32.610] <3576376> GET WARNING: get user info timeout
 Async request: Unable to fetch cache: connection error
400-Bad Request
[2011.10.14 18:55:02.889] <2299921> WARNING: timeout: outdated
[2011.10.14 20:42:55.658] <2293451> WARNING: timeout: outdated
400-Bad Request
 Async request: Unable to fetch cache: connection error
[2011.10.14 20:48:11.743] <3061646> WARNING: rd:0 qu:2 qm:0 qc:0 qd:0 modcount timeout: outdated
[2011.10.14 23:40:34.232] <3575908> GET WARNING: get user info timeout
[2011.10.14 23:05:24.114] <3576777> WARNING: rd:0 qu:0 qm:3 qc:0 qd:0 modcount timeout: outdated
[2011.10.14 23:06:11.614] <3263823>  POST 401-Username or password not valid.
[2011.10.14 23:06:12.102] <3214536> POST 401-Username or password not valid.
[2011.10.14 23:07:05.234] <4232094> POST 401-Username or password not valid.
[2011.10.14 23:12:12.423] <4242500> POST 401-Username or password not valid.
[2011.10.14 23:16:20.324] <2392125> POST 401-Username or password not valid.
[2011.10.14 23:30:33.942] <4839213> WARNING: modcount expired
400-Bad Request
Error message: Can't connect to server. Nslookup failed
[2011.10.14 23:42:34.232] <3457356> WARNING: rd:0 qu:1 qm:0 qc:0 qd:0 modcount timeout: outdated
GET Error message: Can't connect to server. Nslookup failed
GET Error message: Can't connect to server. Nslookup failed
GET Error message: Can't connect to server. Nslookup failed
[2011.10.14 23:45:22.231] <3372947> WARNING: user checking failed  : State DISCONNECTED



Thank you

---

### Post by Dangertux on 2011-11-01
Homework...again...several people posted manuals for and examples for awk...

---

### Post by Lars Noodén on 2011-11-01
This seems like homework.  Is it?

[http://manpages.ubuntu.com/manpages/oneiric/en/man1/awk.1posix.html](http://manpages.ubuntu.com/manpages/oneiric/en/man1/awk.1posix.html)

[http://www.catonmat.net/blog/awk-one-liners-explained-part-one/](http://www.catonmat.net/blog/awk-one-liners-explained-part-one/)

---

### Post by Elfy on 2011-11-01
Closed - homework.

---

