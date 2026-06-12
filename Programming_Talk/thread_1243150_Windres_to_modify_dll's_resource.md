---
title: "Windres to modify dll's resource?"
date: 2009-08-18
forum: Programming Talk
---

### Post by electronixtar on 2009-08-18
Hi guys

I exported resource using windres

```
windres sample.dll sample.rc
```

Then I modified sample.rc using some shellscript

Now I need to compile sample.rc back to sample.dll:

```
windres sample.rc sample.dll
```

turns out sample.dll is corrupted.

Can windres only convert .r to .o ?

I am running in a restricted server without WINE, is there a way to modify .dll/.exe like ResHacker under Liunx?

Thanks in advance.

---

