---
title: "Firefox Won't Start After Update!"
date: 2008-09-24
forum: New to Ubuntu
---

### Post by WBL on 2008-09-24
I just updated Firefox with the Update Manager, and now Firefox won't launch.  Any ideas?

-WBL

---

### Post by billgoldberg on 2008-09-24
> **WBL said:**
> I just updated Firefox with the Update Manager, and now Firefox won't launch.  Any ideas?

-WBL

Open up a terminal (applications -> accessories -> terminal) and type "firefox".

Then post the error message here.

---

### Post by WBL on 2008-09-24
> **billgoldberg said:**
> Open up a terminal (applications -> accessories -> terminal) and type "firefox".

Then post the error message here.

Hmmm...no error messages at all.  Firefox just won't start!

-WBL

---

### Post by superprash2003 on 2008-09-24
open gnome-system-monitor and see if there are any firefox services open.. if so end all firefox services and try opening again

---

### Post by WBL on 2008-09-24
Strange...I restarted my computer and now Firefox works fine.

-WBL

---

### Post by jahst on 2008-12-13
Mine was a permissions issue.
I the ~/.mozilla folder was owned by root so user couldnt open it.

I changed the owner and group recursively to match username and it started right up.

---

