---
title: "help with curl"
date: 2014-06-23
forum: Programming Talk
---

### Post by peter_brickles on 2014-06-23
hi guys im trying to automate a request with curl on the site 

[http://fca-consumer-credit-interim.force.com/CS_RegisterSearchPageNew](http://fca-consumer-credit-interim.force.com/CS_RegisterSearchPageNew)

the ip refernece i have that returns a result is 637235

and the code ive been trying 

> 

curl --data "j_id0:j_id5:j_id22:fnum=637235&press=%20OK%20"  "http://fca-consumer-credit-interim.force.com/CS_RegisterSearchPageNew"





---

### Post by peter_brickles on 2014-06-24
any other way to do this without curl ?

---

### Post by Lars Noodén on 2014-06-24
wget has a lot of options and, unlike curl, comes included by default in Ubuntu.

---

