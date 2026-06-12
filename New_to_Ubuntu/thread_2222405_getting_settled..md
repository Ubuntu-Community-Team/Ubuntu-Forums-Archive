---
title: "getting settled."
date: 2014-05-06
forum: New to Ubuntu
---

### Post by Timothy_Cota on 2014-05-06
1. How do I remove a thread once the problem has been resolved?

2. How does one find a printers' URI?

---

### Post by stalkingwolf on 2014-05-06
1. just mark it solved.

2. go to system >Printing > right click your printer icon and select properties.

---

### Post by slickymaster on 2014-05-06
> **Timothy_Cota said:**
> 1. How do I remove a thread once the problem has been resolved?

You don't remove it. Once you get your problem solved, scroll to the top of your thread and look for the **Thread Tools** menu item on the right of the toolbar, click on this menu item to produce a dropdown menu and finaly click the _"Mark this thread as solved"_ option. This will mark your thread as solved.

> **Timothy_Cota said:**
> 2. How does one find a printers' URI?

Is it a network printer or directly connected to the computer? If directly connected, try localhost or 127.0.0.1

---

### Post by deadflowr on 2014-05-06
> **slickymaster said:**
> 
Is it a network printer or directly connected to the computer? If directly connected, try localhost or 127.0.0.1

Adding to this, if it's a network printer, perhaps look at CUPS.
Open a browser and input this in the url / address bar
```
localhost:631
```

You'll get the CUPS page, where you can configure and setup your network printer(s).

---

