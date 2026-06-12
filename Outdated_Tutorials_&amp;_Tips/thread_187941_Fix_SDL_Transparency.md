---
title: "Fix SDL Transparency"
date: 2006-06-03
forum: Outdated Tutorials &amp; Tips
---

### Post by SaadN on 2006-06-03
[CENTER]**First off all, I do not take any credit for this fix.**[/CENTER]
[COLOR="DarkRed"][B]
Information:[/B][/COLOR]
This fix will make all the programs which run the SDL library into opaque windows, rather than transparent (most games).
[COLOR="DarkRed"][B]
How to fix:[/B][/COLOR]
Simply run this command in the terminal before starting your program.

```
export XLIB_SKIP_ARGB_VISUALS=1
```
[B]
Note: This is a temporary fix.[/B]

Good luck! :)

---

### Post by floam on 2006-06-04
A better fix would be if someone would put together a new .deb package of libsdl for the new 1.2.10 release, which fixes this problerm for real.

---

### Post by SaadN on 2006-06-04
Probably so, but as I said this is a temporary fix. So unless you are up to the job, we might as well use this. :)

---

