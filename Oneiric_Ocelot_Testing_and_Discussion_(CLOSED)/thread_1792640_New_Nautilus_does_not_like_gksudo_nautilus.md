---
title: "New Nautilus does not like gksudo nautilus"
date: 2011-06-28
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by sparker256 on 2011-06-28
```

bill@billsim-1110-64:~$ gksudo nautilus
glibtop: Non-standard uts for running kernel:
release 3.0-2-generic=3.0.0 gives version code 196608

Initializing nautilus-gdu extension
** (nautilus:2839): DEBUG: Syncdaemon not running, waiting for it to start in NameOwnerChanged

(nautilus:2839): GLib-GIO-CRITICAL **: g_file_has_prefix: assertion `G_IS_FILE (file)' failed

(nautilus:2839): GLib-GIO-CRITICAL **: g_file_has_prefix: assertion `G_IS_FILE (file)' failed
bill@billsim-1110-64:~$

```

Bill

---

### Post by ronacc on 2011-06-28
I had a similar problem to that on lubuntu oneiric a couple of days ago , an update cured it .

---

