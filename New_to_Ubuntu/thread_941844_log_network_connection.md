---
title: "log network connection"
date: 2008-10-08
forum: New to Ubuntu
---

### Post by _sphinx_ on 2008-10-08
Just curious!! how do we log all the incoming and outgoing connection of computer?
Is there some command?
TIA.

---

### Post by secondstage on 2008-10-08
[Try this out.]("http://www.cyberciti.biz/faq/linux-tcpip-connection-monitor-howto/")

---

### Post by uncannybuzzard on 2008-10-08
check out tcpdump or tshark.

to monitor an interface and the connections it makes do

```
tcpdump -i eth0 [or whatever your interface is called]
```

---

