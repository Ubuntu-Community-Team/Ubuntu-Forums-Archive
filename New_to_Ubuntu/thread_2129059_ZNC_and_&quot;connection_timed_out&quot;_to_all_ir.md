---
title: "ZNC and &quot;connection timed out&quot; to all irc servers"
date: 2013-03-25
forum: New to Ubuntu
---

### Post by xl8r on 2013-03-25
Hi,

during last weekend I reinstalled my server and after a fresh install of Ubuntu 12.04.2 LTS my bouncer can't connect to any servers. I'm using ZNC and I can connect to it, but ZNC can't connect to any irc servers.

I keep getting this:

```
11:10 <*status> Attempting to connect to [irc.nbl.fi 6667] ...
11:11 <*status> IRC connection timed out.  Reconnecting...

```

I can connect to irc directly by using irssi, so there should not be anything wrong with servers intenet connection. All the rules in iptables are the same that were before reinstall and I'm using same ports for ZNC.

I have no idea where to start looking for the cause of this problem, please help.

---

### Post by stowelly on 2013-03-27
I had this same problem and came across your post when trying to find out what it was..... I solved it by installing znc from source and removing the one I installed from apt

---

