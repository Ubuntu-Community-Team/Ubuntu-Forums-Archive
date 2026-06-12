---
title: "HOWTO: Fix the scroll up - page back bug in Firefox 1.5.0.1"
date: 2006-02-24
forum: Outdated Tutorials &amp; Tips
---

### Post by majikstreet on 2006-02-24
Hey,
There is a big bug in Firefox 1.5.0.1! When you scroll up with a scroll wheel, part of the time the page will go back just like if you had hit "back."

It's not that hard to fix!

Here's how:
1. type about:config into the address bar
2. type mousewheel.horizscroll.withnokey.action in the filter bar
3. right click on the entry that appears
4. choose modify
5. change 2 to 0
6. restart firefox

all done!

**special thanks to darkmatter**

majikstreet

---

