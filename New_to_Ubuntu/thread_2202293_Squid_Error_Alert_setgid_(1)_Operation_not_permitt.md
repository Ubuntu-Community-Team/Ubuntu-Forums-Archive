---
title: "Squid Error Alert: setgid: (1) Operation not permitted"
date: 2014-01-28
forum: New to Ubuntu
---

### Post by Noe_Lana on 2014-01-28
(First Post)

Good day to all Ubuntu Users:

I'm installing squid3 on my Ubuntu Server 12.04 LTS acting as transparent proxy server.

with settings:

**cache_effective_user proxy**
[B]cache_effective_group proxy

[/B]
**sudo chown proxy:proxy **[B]/home/precise/cache/

[/B]Everytime I check using  squid3 -k parse command[B] I get this error:

ALERT: setgid (1) Operation not permitted.

Any opinion and solutions?

Thanks
[/B]

---

