---
title: "Where firefox saves the proxy details"
date: 2010-02-06
forum: Packaging and Compiling Programs
---

### Post by vksingh on 2010-02-06
Hi,

Can anybody tell me in which file firefox browser in ubuntu saves the proxy details(http proxy and ftp proxy).

I want to make a script so that I can change my proxy of browser through the file itself.

Thanks,

Vivek

---

### Post by SevenMachines on 2010-02-07
hi there, its probably the wrong forum to get some more answers on this (maybe the [programming forum]("http://ubuntuforums.org/forumdisplay.php?f=39")? i dont know :) ). but, you should check out the file,
~/.mozilla/firefox/<your-profile-name>/prefs.js

user proxy settings (it they've been set in firefox) will probably look something like,

user_pref("network.proxy.http", "<some.proxyserver.org>");
user_pref("network.proxy.http_port", <port-number>) ;

---

### Post by Brandon Williams on 2010-02-07
Depending upon what you're trying to do, it might be worthwhile looking into [proxy pac files](http://www.returnproxy.com/proxypac/), which allow you to tell the browser how to dynamically select a proxy to use. An even easier solution is [foxyproxy](http://foxyproxy.mozdev.org/index.html), which allows you to define a set of proxies and rules for switching among them.

---

