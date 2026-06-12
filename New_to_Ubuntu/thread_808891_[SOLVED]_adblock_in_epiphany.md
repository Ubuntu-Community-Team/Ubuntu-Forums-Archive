---
title: "[SOLVED] adblock in epiphany?"
date: 2008-05-26
forum: New to Ubuntu
---

### Post by golgo13 on 2008-05-26
is it possible to enable adblocking in epiphany like you can in firefox?

---

### Post by meltindar on 2008-05-27
In epiphany go to Tools>Extensions and activate 'Ad Blocker' extension. If you don't have it you should install epiphany-extensions package.
```
sudo apt-get install epiphany-extensions
```

HTH

---

### Post by meltindar on 2008-05-27
Also there was a bug for this [https://bugs.launchpad.net/ubuntu/+source/epiphany-extensions/+bug/194050](https://bugs.launchpad.net/ubuntu/+source/epiphany-extensions/+bug/194050) but looks like they've fixed it. If your add blocker doesn't work, simply update the extensions package and it will work again.

---

### Post by golgo13 on 2008-05-27
thanks
I downloaded the extension but...
I don't know where the tools menu is in epiphany :redface:
I assumed its under preferences but cannot find it
I am using Web Browser 2.20.1 if that helps

---

### Post by meltindar on 2008-05-28
Well I use 2.22.1.1. but the Tool's menu is there for quite some time now :)
It's a separate menu on main menu bar, right next to Bookmarks and before Tabs :)
It only has one submenu and that's Extensions.

HTH

---

### Post by golgo13 on 2008-05-28
thanks for the help
tools wasn't there (was it?!) until I reloaded today
maybe I couldn't see the wood for the trees or something....:confused:
but thanks anyway appreciate it

---

### Post by meltindar on 2008-05-29
Most probably it shows up only when you have the epiphany-extensions package(and then restart browser) :(
sorry my bad ...

---

### Post by golgo13 on 2008-05-29
no worries :)

---

