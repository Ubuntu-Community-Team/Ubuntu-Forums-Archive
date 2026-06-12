---
title: "Upgrade to 11.10 Cannot run Nautilus as root"
date: 2011-07-30
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Rifester on 2011-07-30
Cannot open Nautilus with gksu nautilus or gksudo nautilus.  Here is terminal output:

(gksudo:25518): GConf-WARNING **: Client failed to connect to the D-BUS daemon:
Failed to connect to socket /tmp/dbus-nZ9CFRmQIP: Connection refused
GConf Error: No D-BUS daemon running


(gksudo:25518): GConf-WARNING **: Client failed to connect to the D-BUS daemon:
Failed to connect to socket /tmp/dbus-nZ9CFRmQIP: Connection refused
GConf Error: No D-BUS daemon running


(gksudo:25518): GConf-WARNING **: Client failed to connect to the D-BUS daemon:
Failed to connect to socket /tmp/dbus-nZ9CFRmQIP: Connection refused
GConf Error: No D-BUS daemon running


(gksudo:25518): GConf-WARNING **: Client failed to connect to the D-BUS daemon:
Failed to connect to socket /tmp/dbus-nZ9CFRmQIP: Connection refused
GConf Error: No D-BUS daemon running


(gksudo:25518): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed
** (nautilus:25520): DEBUG: Syncdaemon not running, waiting for it to start in NameOwnerChanged
Initializing nautilus-gdu extension

(gksudo:25518): GConf-WARNING **: Client failed to connect to the D-BUS daemon:
Failed to connect to socket /tmp/dbus-nZ9CFRmQIP: Connection refused
GConf Error: No D-BUS daemon running

Any ideas?

---

### Post by fjgaude on 2011-07-30
No ideas, except hopefully it will not continue will not last. Likely in Alpha 3 it will be fixed.

Also I don't think links work either. <smile>

---

### Post by jerrrys on 2011-07-30
this is probably 10.10 specific, but just a thought.  

in gconf-editor, under  apps > gksu. Is the 	'sudo-mode' box ticked?

---

### Post by Rifester on 2011-07-30
It is checked...  I did find some bugs where this is affecting others.   Hope we have a fix soon!

---

### Post by drs305 on 2011-07-30
I am not getting nautilus-gksu to work either, so I'm using pcmanfm as my root file browswer, which runs fine with gksu.

---

### Post by mc4man on 2011-07-30
> **Rifester said:**
> It is checked...  I did find some bugs where this is affecting others.   Hope we have a fix soon!There are probably a few bugs on this, the most common is here
[https://bugs.launchpad.net/nautilus/+bug/804330](https://bugs.launchpad.net/nautilus/+bug/804330)
though many times this is seen either in terminal or sometimes .xsession-errors
> (nautilus:3298): GLib-GIO-CRITICAL **: g_file_has_prefix: assertion `G_IS_FILE
(file)' failed
Your error is a bit different..
(you could look in /var/crash for a nautilus .crash though there are other current nautilus crashes going on not related to gksu

For whatever reason many installs can open a root nautilus, both of mine can, 1 is 6 days old, the other 11.04 upgraded about 2 weeks ago.
Though I wouldn't be surprised if I did a fresh install w/ todays iso it wouldn't work

Overall I prefer using the nautilus-gksu extension  over running gksu(do)-nautilus, if one can open a root nautilus then the nautilus-gksu extension is workable by having a /usr/lib/nautilus/extensions-3.0/libnautilus-gksu.so in place
(though gksu could use a proper rebuild

---

### Post by Xgen on 2011-08-02
Finally...just noticed that it works now, though now I've got used to Marlin as root.

Note: Please test and mark [Solved] if satisfied.

---

### Post by drs305 on 2011-08-02
> **Xgen said:**
> Finally...just noticed that it works now, though now I've got used to Marlin as root.

There was an update to deja-dup today that supposedly fixed this issue. It did for me...

---

### Post by fjgaude on 2011-08-02
Yep, it's fixed: we can have a root Nautilus! Hurrah!

---

### Post by Rifester on 2011-08-02
Confirmed! Today's updates fixed it!

---

