---
title: "cannot access web server in libupnp"
date: 2009-02-22
forum: Programming Talk
---

### Post by studious on 2009-02-22
Dear all,
I have a problem with webserver built inside libupnp.

I use ushare as media server. The ushare uses built-in web server of libupnp. After I start ushare, I try to access usahre via web by [http://my_ip:49200/web/ushare.html](http://my_ip:49200/web/ushare.html). The page cannot open.
But [http://localhost:49200/web/ushare.html](http://localhost:49200/web/ushare.html) is OK.

I think this problem is from libupnp. 
Could anyone tell me why I cannot access web via [http://my_ip:49200/web/ushare.html?](http://my_ip:49200/web/ushare.html?)


Here is what ushare starts:

[user1@home-srv ushare]$ ushare -f /etc/ushare.conf Interface eth0 is down.
Recheck uShare's configuration and try again !
uShare (version 1.1a), a lightweight UPnP A/V and DLNA Media Server.
Benjamin Zores (C) 2005-2007, for GeeXboX Team.
See [http://ushare.geexbox.org/](http://ushare.geexbox.org/) for updates.
Listening on telnet port 1337
Initializing UPnP subsystem ...
UPnP MediaServer listening on 10.88.32.12:49200 Sending UPnP advertisement for device ...
Listening for control point connections ...
Building Metadata List ...
Looking for files in content directory : /home/user1/private_data Found 17 files and subdirectories.

---

