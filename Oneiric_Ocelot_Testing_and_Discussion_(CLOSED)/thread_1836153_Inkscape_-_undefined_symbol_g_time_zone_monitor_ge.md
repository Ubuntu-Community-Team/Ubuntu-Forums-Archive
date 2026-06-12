---
title: "Inkscape - undefined symbol: g_time_zone_monitor_get_type"
date: 2011-08-30
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by garthecho on 2011-08-30
After an upgrade to Oneiric, I'm getting "undefined symbol: g_time_zone_monitor_get_type" when trying to start Inkscape.  Anyone else seeing this?

---

### Post by MacUntu on 2011-08-30
Starts fine here on amd64.

---

### Post by garthecho on 2011-08-30
That's what I was afraid of.  I don't see the bug anywhere else on the web, so I fear it's time for a reinstall. [SIZE="1"]dang it![/SIZE]

---

### Post by fjgaude on 2011-08-30
Yes, both Gimp and Inkscape work here as they should, x64, 3D, latest update.

---

### Post by MadCow108 on 2011-08-30
reinstalling libglib2.0-0 might help:

```
~$ nm --dynamic /usr/lib/x86_64-linux-gnu/libgio-2.0.so  | grep g_time_zone_monitor_get_type
000000000007bca0 T g_time_zone_monitor_get_type
~$ dpkg -S libgio-2.0.so
libglib2.0-dev: /usr/lib/x86_64-linux-gnu/libgio-2.0.so
libglib2.0-0:i386: /usr/lib/i386-linux-gnu/libgio-2.0.so.0.2916.0
libglib2.0-0:i386: /usr/lib/i386-linux-gnu/libgio-2.0.so.0
libglib2.0-0: /usr/lib/x86_64-linux-gnu/libgio-2.0.so.0
libglib2.0-0: /usr/lib/x86_64-linux-gnu/libgio-2.0.so.0.2916.0

```

sudo apt-get install --reinstall libglib2.0-0

also check if inkscape is linked against libgio with ldd /usr/bin/inkscape

---

### Post by garthecho on 2011-08-30
Thanks for the tips.  None of the above is working so I'm getting ready for a fresh install.  I'll be back if the problem is still there. :)

---

