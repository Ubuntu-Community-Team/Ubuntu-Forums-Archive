---
title: "Web pages opening slow in Ubuntu 12.04"
date: 2013-06-07
forum: New to Ubuntu
---

### Post by mountainman70 on 2013-06-07
Dell Optiplex 745 running dual boot Wxp Sp3 and Ubuntu 12.04.

Lately it seems that my web pages in Ubuntu 12.04 are taking several seconds to open. In Wxp everything seems to open instantaneous. I have done a search but do not understand what I should try or how to do it. I have not paid much attention as to how long this has been happening. I think it started after an update sometime back, but am not sure. I just know Ubuntu used to be faster than Windows.

Any help is appreciated.

---

### Post by tgalati4 on 2013-06-08
What browser are you using?  Is IPV6 turned off?  If running firefox, try opening [http://about:config](http://about:config) and search on IPV, then post the status of the switches.

Try clearing your cache and your history.  Try a different browser.

---

### Post by mountainman70 on 2013-06-08
> **tgalati4 said:**
> What browser are you using?  Is IPV6 turned off?  If running firefox, try opening [http://about:config]("http://about<strong></strong>:config") and search on IPV, then post the status of the switches.

Try clearing your cache and your history.  Try a different browser.

I am running FF 21.0. Cache and history are cleared. I also have 3gb of ram.

about:config IPV
network.dns.disableIPv6;false
network.dns.ipv4OnlyDomains;string
network.http.fast-fallback-to-IPv4;true

---

### Post by mountainman70 on 2013-06-08
After trying another browser and every web page opening fast, I decided to see if any of my FF extensions could be the problem. I disabled all FF extensions and then restarted FF. Every page opened fast. I determined that an old adblock extension I was using was the problem. I removed it and installed Adblock Plus and all pages seem to be opening fast now.

Thanks tgalati4 for responding.

---

