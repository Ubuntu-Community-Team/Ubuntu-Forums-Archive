---
title: "rc question about concurrency"
date: 2011-09-16
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Rocksinboxes on 2011-09-16
Hi,

    I was wondering if anyone knew if changing the concurrency=make to shell in /etc/init.d/rc would make any difference on performance. I noticed that 'none' is no longer the default. If you could please let me know that would be great. thanks.

---

### Post by oldos2er on 2011-09-16
"shell" is obsolete, and actually it was changed some time ago:

# Specify method used to enable concurrent init.d scripts.
# Valid options are 'none' and 'makefile'.  Obsolete options
# used earlier are 'shell' and 'startpar'.  The obsolete options
# are aliases for 'makefile' since 2010-05-14.  The default since
# the same date is 'makefile', as the init.d scripts in Debian now
# include dependency information and are ordered using this
# information.  See insserv for information on dependency based
# boot sequencing.

I leave mine at CONCURRENCY=makefile

---

