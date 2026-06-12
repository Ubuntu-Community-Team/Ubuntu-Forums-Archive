---
title: "Third Party software 14.01"
date: 2014-04-29
forum: New to Ubuntu
---

### Post by maclinuxman on 2014-04-29
When doing the installation of version 14.01 it states about third party software being turned off.  Do I need to do something to reactivate these after the installation?  thanks

---

### Post by LastDino on 2014-04-29
You mean 14.04? Install ''restricted extra'' from software centre.

---

### Post by ibjsb4 on 2014-04-29
> **maclinuxman said:**
> When doing the installation of version 14.01 it states about third party software being turned off.  Do I need to do something to reactivate these after the installation?  thanks

Yes, probably so, some may not have a 14o4 version, some may need an upgrade.  Upgrades to 14o4 can cause system breakage.  It is generally considered a good idea to wait till 14.04.01 comes out.  Just a thought :)

You can list of all installed ppa's in terminal.

```
ls /etc/apt/sources.list.d/*.list
```

Edit:  Third party software can also show up in /etc/apt/sources.list

---

