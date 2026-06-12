---
title: "configure &quot;critically low battery&quot;"
date: 2011-12-20
forum: New to Ubuntu
---

### Post by broshe on 2011-12-20
Hello,
Is there a way to configure the "critically low" battery power.
That is how can I set the the critically low level to be 5% or 10% of the total power or 10 minutes remaining?

I am using ubuntu 10.04

Thanks
Eli

---

### Post by lechien73 on 2011-12-20
To change what Ubuntu determines as the critical level for your battery, do the following:

Press Alt+F2. In the "Command" dialog box, type:

```
gconf-editor
```

Navigate to **apps -> gnome-power-manager -> thresholds**

There you will find keys for the percentage of battery power for determining low and critical states, and also keys for the run-time remaining.

Adjust the figures as desired. If you want to use percentage rather than time for determining how when to shut down, then uncheck the *use-time-for-policy* key.

---

