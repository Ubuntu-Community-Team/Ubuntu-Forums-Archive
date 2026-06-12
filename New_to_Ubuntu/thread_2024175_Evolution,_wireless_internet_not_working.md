---
title: "Evolution, wireless internet not working"
date: 2012-07-13
forum: New to Ubuntu
---

### Post by chitragurung on 2012-07-13
Hello,

I have been using ubuntu 10.04 in dell mini 10 machine.

My bluetooth was not working so I uninstall the Blue tooth items from software list after than

Evolution could not open. Error message display when click on icon.
Wire less network not working. No internet. Wireless network manager also not appeared.

---

### Post by Cheesehead on 2012-07-13
Look in /var/log/history/apt or in Synaptic --> History for the history file for that date.

It will tell you what you actually removed.
Perhaps you removed much more than you intended to?

---

### Post by chitragurung on 2012-07-13
i have var/log/apt

How to reinstall  it ?

---

### Post by Cheesehead on 2012-07-14
sudo apt-get install package1 package2 package3

The packages, uninstalled, are usually still in your /var/cache/apt/archive (unless you cleaned out your apt cache), so can be reinstalled without a network connection.

If you need more specific advice, please post the history file showing what you removed.

---

### Post by chitragurung on 2012-07-14
I uninstalled bluetooth. Nothing other. But where and how can i find history ?

---

### Post by Cheesehead on 2012-07-14
If all you actually removed was bluetooth, then you wouldn't have this problem.

CORRECTION: The history file is in /var/log/apt/history  (Thanks, arpanaut!)

---

### Post by arpanaut on 2012-07-14
> **Cheesehead said:**
> If all you actually removed was bluetooth, then you wouldn't have this problem.

The history file is in /var/log/history/apt

The history file is /var/log/apt/history.log  ):P

To see the contents:

```
cat /var/log/apt/history.log
```

---

