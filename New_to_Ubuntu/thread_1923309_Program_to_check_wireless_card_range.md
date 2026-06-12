---
title: "Program to check wireless card range?"
date: 2012-02-10
forum: New to Ubuntu
---

### Post by Wiking on 2012-02-10
Is there any program for Linux that I could use to check the range on my wireless card?

---

### Post by cariboo on 2012-02-10
Typical range with a stock antenna is about 100ft. If your device supports it, you can use iwspy to collect data about wireless access points that are in range.

```
iwspy <interface>
```

where <interface> = your wirless interface. I have several wireless devices, and the only one that is support is a D-Link.

---

### Post by Zill on 2012-02-11
> **Wiking said:**
> Is there any program for Linux that I could use to check the range on my wireless card?
[iwScanner]("http://kuthulu.com/iwscanner") is a wireless scanner for linux with an easy to use graphic interface.

(Ubuntu deb download available)

---

