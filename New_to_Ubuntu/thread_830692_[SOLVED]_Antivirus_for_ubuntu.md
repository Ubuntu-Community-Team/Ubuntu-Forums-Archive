---
title: "[SOLVED] Antivirus for ubuntu??"
date: 2008-06-16
forum: New to Ubuntu
---

### Post by bkamalnivas on 2008-06-16
Is ther any antivirus for Ubuntu that i can install??

---

### Post by akiratheoni on 2008-06-16
You can install clamav:

```
sudo apt-get install clamav
```

But to be honest you don't need ANY anti-virus whatsoever for Linux unless you're running a file or mail server.

EDIT: Good read: [http://www.theregister.co.uk/2003/10/06/linux_vs_windows_viruses/](http://www.theregister.co.uk/2003/10/06/linux_vs_windows_viruses/)

---

### Post by vishzilla on 2008-06-16
You don't need antivirus programs in Linux unless you have some Windows machines in your network. [https://help.ubuntu.com/8.04/keeping-safe/C/index.html](https://help.ubuntu.com/8.04/keeping-safe/C/index.html)

---

### Post by quinnten83 on 2008-06-16
*sigh*
yes there is, but Linux itself doesn't need an antivirus, as most virri are written for windows and the structure of linux is such that it's very difficult to create a working virus for it.
you can check in add/remove for clamav or on the avg website where you can download a .deb.

---

### Post by ChameleonDave on 2008-06-16
> **quinnten83 said:**
> most virri are written for...

That's a rather creative spelling of "[viruses]("http://en.wikipedia.org/wiki/Plural_of_virus")".

------

I'd add that *klamav* is a good KDE frontend to *clamav*.

---

### Post by bkamalnivas on 2008-06-16
Thanx a lot

---

### Post by akiratheoni on 2008-06-16
> **bkamalnivas said:**
> Thanx a lot

No problem, don't forget to mark this thread as solved please :) Thanks.

---

### Post by skymera on 2008-06-16
AVG do a nice anti-virus.

But most Linux clients only scan for Windows viruses on Windows parititons.

I used to have AVG Linux to scan my XP because it was so much quicker.

---

