---
title: "How-to: easy tweaks to make firefox run faster."
date: 2008-09-01
forum: New to Ubuntu
---

### Post by dankster117 on 2008-09-01
My firefox browser was running extremely slow when trying to load pages so I searched all over the web to look for some tweaks to make it run faster and would like to share it with you, here is what I have found.

Open up your firefox web browser, and in the address bar type
```
about:config
```
now on the config page change these following entries to true (by double clicking them)
```
network.http.pipelining
```
```
network.http.proxy.pipelining
```
now change
```
network.http.pipelining.maxrequests
``` to 30
now right click anywhere on the page and select new integer. in the dialog box type
```
nglayout.initialpaint.delay
```
when the other dialog box appears enter 0 (zero)

restart the browser and it should run much faster! (well it did in my case)

---

### Post by ~LoKe on 2008-09-01
Should be in the Tips and Tricks forum, actually, it is, posted by several people. ;)

---

### Post by steveneddy on 2008-09-01
Yeah - this is an old one.

---

### Post by Perfect Storm on 2008-09-02
Thread closed.

There's alot of guides/howtos in our Tutorials & Tips forum regarding tweaking firefox.

---

