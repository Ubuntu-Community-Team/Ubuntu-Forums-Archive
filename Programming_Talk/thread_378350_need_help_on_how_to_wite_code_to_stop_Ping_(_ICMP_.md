---
title: "need help on how to wite code to stop Ping ( ICMP )"
date: 2007-03-07
forum: Programming Talk
---

### Post by Prince James on 2007-03-07
Hello all ! im new here and this forum looks really good for what im studying at university ! can someone give me information or write a basic code for me on how to stop pepole from Pinging  the network !!!

im using Html Kit just to let you guys know ! OS Fedora core 6 !!! :)

---

### Post by cronholio on 2007-03-07
You don't need to program anything. Install iptables and disallow pinging.

```
deny icmp any any echo-request
```

---

### Post by Prince James on 2007-03-07
thats it ? dam i tho it's going to be some long code !!!

---

### Post by ghostdog74 on 2007-03-07
not going to give u sample code, but just an idea to get started. search for ipchains, download the source, and take a look at how its written. maybe you can get an idea.

---

### Post by Prince James on 2007-03-07
ok cheers m8 ! :popcorn: :popcorn:

---

