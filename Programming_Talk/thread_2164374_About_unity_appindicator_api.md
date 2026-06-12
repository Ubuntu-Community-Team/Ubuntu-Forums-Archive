---
title: "About unity appindicator api ?"
date: 2013-07-31
forum: Programming Talk
---

### Post by prismctg on 2013-07-31
Hi , I m developing a node.js application for ubuntu desktop . Is there any unity appindicator api for javascipt ? Or how do I implement appindicator in node.js ... any suggestion ?

---

### Post by ian-weisser on 2013-07-31
AppIndicators use dbus to communicate with the system, and to communicate with the application they indicate for. Look for javascript-dbus bindings. A quick search turned up many possibles for you.

---

