---
title: "HOWTO: fix freezes on recursive queries with MaraDNS"
date: 2005-09-13
forum: Outdated Tutorials &amp; Tips
---

### Post by nocturn on 2005-09-13
I have been running MaraDNS since I intalled my Ubuntu server, it is a nice DNS server that also offers recursive queries.

At random times, it freezes waiting on an answer from the upstream DNS.  This appears to be due to a bug in the Linux kernel.  
There is a workarround in the latest version of MaraDNS, but this is neither availble for Hoary as for Breezy.

To get arround this problem, get the RPM for the latest version from the MaraDNS site (currenly 1.0.32) and use alien to convert it to a deb file.
Now remove the old version (without purging your config) and install the new one.

Restart MaraDNS, and your problems should be solved.

Have fun.

---

