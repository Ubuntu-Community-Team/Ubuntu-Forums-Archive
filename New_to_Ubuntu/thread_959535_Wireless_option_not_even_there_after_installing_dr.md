---
title: "Wireless option not even there after installing drivers"
date: 2008-10-26
forum: New to Ubuntu
---

### Post by derek0 on 2008-10-26
New to ubuntu. Managed to find my wireless card's driver and install it via windows wireless drivers. It says installed and hardware present.

So what do I do now? For some reason, the Network settings box never has a wireless connection at all. So I can't configure anything. Can I force something to look at the driver and the card and use it, or what? No walkthrough I've tried so far has worked.

---

### Post by Xiong Chiamiov on 2008-10-29
If you do a 
```

ifconfig -a

```
do you get anything besides eth0 and lo?

---

### Post by macogw on 2008-10-29
Did you reboot after installing the driver?

---

### Post by bumanie on 2008-10-29
Did you use ndiswrapper and its gtk frontend? That's the easiest way to get windows drivers working with your card. What is the wifi card?

---

