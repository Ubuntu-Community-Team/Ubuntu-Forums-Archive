---
title: "Synaptic installing error"
date: 2008-08-23
forum: New to Ubuntu
---

### Post by NWAdawg on 2008-08-23
I have a Synaptic error that reads every time I install a package. 
error reads:

"debconf: unable to initialize frontend: Dialog
(Dialog frontend will not work on dump terminal , an emac shell buffer, or without a controlling terminal 
deconf: falling back to frontend: Readline
Selecting previously deselected package ****"

Then it goes on to reading database and installing package.
I get this with or without Dialog installed. 
How I fix it?

---

### Post by mr.moch on 2008-08-23
I'm not sure if this will work, but try:

```
sudo dpkg --configure -a
```

See how it works.....as long as it still installs the package, it's not a big ordeal.

---

