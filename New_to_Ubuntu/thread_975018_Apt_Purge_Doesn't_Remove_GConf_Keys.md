---
title: "Apt Purge Doesn't Remove GConf Keys?"
date: 2008-11-08
forum: New to Ubuntu
---

### Post by lucasl on 2008-11-08
Hi,
I noticed when using "Complete Remove" (purge) on a package, GCong registry keys aren't removed.
This seems ridiculous to me! Should I file a bug report, or is this a 'feature'.

Thanks!

---

### Post by Martje_001 on 2008-11-08
This is the way it should work. Synaptic only removes system-wide files, not files that are made by the program itself (in your home-directory).

---

### Post by lucasl on 2008-11-08
Really? I was definately under the impression that although remove does this, Complete Remove removes all traces (it does say "including configuration files" when you click apply in synaptic.
Hmmm, I have to check now. *runs off the install and configure, then remove an app*

---

### Post by Jeff250 on 2008-11-08
Martje_001 is correct.  As far as "Removal" vs. "Complete Removal", "Complete Removal" will remove system-wide configuration files, e.g. settings in /etc for the program.  It will not remove users' configuration files, e.g. stuff in /home.

---

### Post by m_l17 on 2008-11-08
Martje_001 and jeff250 are correct. You have to remove the configuration files and or dir manually from your /home dir

---

