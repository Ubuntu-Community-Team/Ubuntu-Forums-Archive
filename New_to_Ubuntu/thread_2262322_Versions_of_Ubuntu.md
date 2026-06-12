---
title: "Versions of Ubuntu"
date: 2015-01-24
forum: New to Ubuntu
---

### Post by adrian46 on 2015-01-24
Hi experts,

I am a new ubuntu user, can anybody tell whats the difference between 

ubuntu-12.04.4-alternate-amd64

ubuntu-12.04.4-desktop-amd64

ubuntu-12.04.4-server-amd64

I am planning to deploy ubuntu 12.4 via wds plz suggest which of the above version will be suitable...???

Thank You....

---

### Post by TheFu on 2015-01-24
[http://releases.ubuntu.com/12.04/](http://releases.ubuntu.com/12.04/) seems to explain nicely.

Don't know what "wds" is. Sorry.

---

### Post by adrian46 on 2015-01-24
Its Windows Deployment Services.

---

### Post by TheFu on 2015-01-24
> **adrian46 said:**
> Its Windows Deployment Services.

Why would you use that for a Linux deployment?  Guess people do it for some reason.

Cobbler [https://help.ubuntu.com/community/Cobbler](https://help.ubuntu.com/community/Cobbler) will perform bare metal installs for large scale deployments.
Then you can use something like ansible to manage all those machines thru 1 simple interface.

---

