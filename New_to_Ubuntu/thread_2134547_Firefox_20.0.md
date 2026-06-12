---
title: "Firefox 20.0"
date: 2013-04-11
forum: New to Ubuntu
---

### Post by Silvertones on 2013-04-11
Ubuntu 10.04 dialup connection. Since the update 2 days ago Firefox now cobstantly opens in "offline mode". I went to about:config and it's set for online yet opens offline. Any ideas? Thanks

---

### Post by KnownSyntax on 2013-04-11
Are you fully made sure that your computer is connected to the internet? If anything it might be a problem with your speeds and FireFox is set to handle a higher speed (and therefore then thinks it's offline because of the painfully slow speeds).

---

### Post by Silvertones on 2013-04-11
> **KnownSyntax said:**
> Are you fully made sure that your computer is connected to the internet? If anything it might be a problem with your speeds and FireFox is set to handle a higher speed (and therefore then thinks it's offline because of the painfully slow speeds). Sure I'm connected.This just started with the v 20.0 update.I suppose it could be some new FF thing that thinks I'm not on line because of the slow connection.

---

### Post by Silvertones on 2013-04-12
OK I misinterpreted what was said or it's been reworded in about:config. You need to set: network-manage offline status to False not true.

---

