---
title: "Code Igniter displays blank pages!"
date: 2008-04-10
forum: Programming Talk
---

### Post by Mickeysofine1972 on 2008-04-10
Hey guys

Anyone used Code Igniter?

I have it working but when I set the $config['log_threshold'] = 0; line to be > 0 I get a blank page and not content.

When it set to 0 its fine though, any idea why?

Mike

[EDIT]

SOLVED: 
the permissions for the system/logs folder where not set to www-data ! DOH!

---

### Post by fortran01 on 2009-02-23
The blank page occurred to me because php5-mysql modules was not installed.

---

