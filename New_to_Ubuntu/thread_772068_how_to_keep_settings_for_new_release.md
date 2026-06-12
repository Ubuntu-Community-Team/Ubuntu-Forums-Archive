---
title: "how to keep settings for new release"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by duruttye on 2008-04-28
Hi!

I'm just downloading the new ubuntu release, but I want to keep all settings, and desktop features without an upgrade?

If i will burn a dvd with /home folder contents and after the install copy the whole thing replacing the new /home folder? Will that work?

Thanx!

---

### Post by skymera on 2008-04-28
Im sure you can upgrade using the CD if you add the CD to your sources.

But a straight upgrade from 7.10 -> 8.04 will keep all settings as they were, bearing the upgrade doesn't go wrong.

---

### Post by Tatty on 2008-04-28
Not nessesarily perfecty as there may be symbolic links which get broken.  You need to put /home into a separate partition if you want to do that [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by hyper_ch on 2008-04-28
user-based settings are stored in their according home folder, so backing up /home and restoring it afterwards will take care of most settings.

However some settings are global and they are stored in /etc... just to make sure, also backup the /etc folder (but don't copy it all back once you've installed the new system... just do it then on a per-need level).

---

