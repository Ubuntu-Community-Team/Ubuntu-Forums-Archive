---
title: "No audio in flashapps"
date: 2008-05-14
forum: New to Ubuntu
---

### Post by Helged on 2008-05-14
When Rhytmbox is running, doesn't necessarely play music, the sounds from flash movies etc isn't working.

This is quite annoying. How can i fix it?

---

### Post by billgoldberg on 2008-05-14
> **Helged said:**
> When Rhytmbox is running, doesn't necessarely play music, the sounds from flash movies etc isn't working.

This is quite annoying. How can i fix it?

Open a terminal and copy/paste this:

```
sudo apt-get install libflashsupport
```

Restart firefox to get flash sound working again.

---

### Post by farueulogy on 2008-05-14
I wish they'd make libflashsupport a dependancy for flashplugin-nonfree on 8.04

---

### Post by billgoldberg on 2008-05-14
> **farueulogy said:**
> I wish they'd make libflashsupport a dependancy for flashplugin-nonfree on 8.04

Me to.

But there seemed to some troubles in the hardy beta's with it, so they removed it as dependency.

It seemed the bug is fixed now, so they should make it a dependency again.

---

