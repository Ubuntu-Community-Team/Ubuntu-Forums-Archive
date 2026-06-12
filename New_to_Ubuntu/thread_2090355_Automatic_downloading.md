---
title: "Automatic downloading"
date: 2012-12-02
forum: New to Ubuntu
---

### Post by kiranmatrixlee on 2012-12-02
i am using ubuntu 12.04 LTS.I noticed that,some time it downloading something from internet.i find out it from system monitor.How to find which file is downloading now?
update manager is disabled at that time.

---

### Post by dodo3773 on 2012-12-02
Some simple commands to help:
Network Processes:
```

ps -o cmd= -p $(lsof -i -n -P | sed 1d | awk '{print $2}' | uniq)

```

Ip Addresses:
```

netstat --tcp --numeric | awk 'NR>2 {print $5}'| sort -n -t : -k 2,2

```

Then do a whois on the ip address. Example:
```

$whois 74.125.25.109
...

NetRange:       74.125.0.0 - 74.125.255.255
CIDR:           74.125.0.0/16
OriginAS:       
NetName:        GOOGLE
NetHandle:      NET-74-125-0-0-1
Parent:         NET-74-0-0-0-0
NetType:        Direct Allocation
RegDate:        2007-03-13
Updated:        2012-02-24
Ref:            http://whois.arin.net/rest/net/NET-74-125-0-0-1

...

```


Just throw it in a while loop in a terminal for a while if you want. Here's a one-liner:
```

while true; do ps -o cmd= -p $(lsof -i -n -P | sed 1d | awk '{print $2}' | uniq) && netstat --tcp --numeric | awk 'NR>2 {print $5}'| sort -n -t : -k 2,2 && sleep 1; done

```
then just ctrl+c to kill it. Hope that helps.

---

### Post by 3rdalbum on 2012-12-02
> **kiranmatrixlee said:**
> i am using ubuntu 12.04 LTS.I noticed that,some time it downloading something from internet.i find out it from system monitor.How to find which file is downloading now?
update manager is disabled at that time.

There's two possibilities:

1. Update Manager sometimes checks for updates periodically, unless you disable that option.

2. Some combinations of wireless card and router are very "chatty" and exchange a lot of data even when there's nothing really happening. If the amount of data being exchanged is small (1-2kbps) then this is probably what's happening. It's nothing to worry about; this information is only travelling across your local network, not to the internet. You can't stop it without changing to a different wireless card or router, but this small amount of data doesn't matter on a home network.

---

