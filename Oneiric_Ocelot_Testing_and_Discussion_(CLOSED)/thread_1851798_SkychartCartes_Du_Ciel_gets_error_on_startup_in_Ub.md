---
title: "Skychart/Cartes Du Ciel gets error on startup in Ubuntu 11.10"
date: 2011-09-29
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by alphacrucis2 on 2011-09-29
Just posting this as a tip to fix this problem. When starting Cartes Du Ciel stable or beta version under Ubuntu 11.10 I received this error:

```
TWinControl.WMSize loop detected, the widgetset does not like the LCL bounds or sends unneeded wmsize messages: HorScrollBar:TScrollBar BoundsRealized=l=0,t=671,r=1226,b=687 NewBoundsRealized=l=0,t=671,r=0,b=687.
```

I contacted the developer and he gave me this solution:

> You can bypass the problem by editing the file ~/.skychart/skychart.ini
Locate the line ViewScrollBar=1
and replace by ViewScrollBar=0
Save the file and now skychart can run correctly.

After this Cartes Du Ciel runs as normal!

---

