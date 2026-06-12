---
title: "A shell script's question"
date: 2007-11-24
forum: Programming Talk
---

### Post by LaoLiulaoliu on 2007-11-24
I want to write a script to let my net.eth0 auto start or stop.
if it start,it will show our school's private like:10.200.*.*
if not,it will show like this:
# ifconfig eth0
eth0   Link encap:Ethernet  HWaddr 00:13:8F:C1:48:94  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:500 errors:0 dropped:0 overruns:0 frame:0
          TX packets:281 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:53002 (51.7 Kb)  TX bytes:28402 (27.7 Kb)
          Interrupt:22 Base address:0xe000 
So I write a script to let it run.

#!/bin/bash
ifconfig eth0 | grep 10.200
if [ "echo $?" = "0" ];then
        /etc/init.d/net.eth0 stop
else
        /etc/init.d/net.eth0 start
fi

But this script always run /etc/init.d/net/eth0 start,I don't know why.

---

### Post by volanin on 2007-11-24
Change this:

**if [ "echo $?" = "0" ];then**

To this:

**if [ "$?" = "0" ];then**

---

### Post by geirha on 2007-11-24
You can pass the command directly to if as well: ```

if ifconfig eth0 | grep 10.200 >/dev/null ; then
    echo stop
else
    echo start
fi
```

---

### Post by LaoLiulaoliu on 2007-11-24
thank you.

---

