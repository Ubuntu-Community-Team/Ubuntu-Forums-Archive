---
title: "Error HP Fax"
date: 2013-03-23
forum: New to Ubuntu
---

### Post by chron3 on 2013-03-23
I uninstalled all HP drivers from my computer, but I still get an error from HP Fax every time I boot my computer. Did I miss anything?


```
Executable Path:
/usr/lib/cups/backend/hpfax

Problem Type:
Crash

Title:
hpfax crashed with NameError in bug(): global name 'log' is not defined
```

---

### Post by gordintoronto on 2013-03-23
I'm pretty sure that message indicates you did not remove all HP drivers from your computer.

What version of Ubuntu? If you run "printers" does the fax appear? How about if you install and run Synaptic Package Manager, and search for "hpfax"?

---

### Post by chron3 on 2013-03-24
I manually searched the hidden folders and found one file that belonged to HP Fax, so I deleted it and now that error message doesn't appear anymore.

---

