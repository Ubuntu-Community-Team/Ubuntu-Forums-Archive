---
title: "indicator-network is mapped two times"
date: 2011-10-08
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by lucazade on 2011-10-08
when I open the indicator-network in Oneiric the menu is displayed two times,
the first contains only few elements then is re-loaded with all correct network-devices.

[https://bugs.launchpad.net/indicator-network/+bug/831323](https://bugs.launchpad.net/indicator-network/+bug/831323)

this bug report didn't get any attention, any confirms?

---

### Post by lucazade on 2011-10-08
found some interesting output:

```
** Message: applet now removed from the notification area
unity-2d-panel: [WARNING] X Error: BadWindow (invalid Window parameter) 3
  Major opcode: 20 (X_GetProperty)
  Resource id:  0x1e00004
** (nm-applet:2204): DEBUG: old state indicates that this was not a disconnect 0
```

---

