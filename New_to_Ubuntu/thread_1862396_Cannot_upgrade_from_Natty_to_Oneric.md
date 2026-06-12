---
title: "Cannot upgrade from Natty to Oneric"
date: 2011-10-16
forum: New to Ubuntu
---

### Post by bigfootnmd on 2011-10-16
SOLVED

On my desktop (not my netbok) I cannot upgrade to Oneric 11.10.

If I click on Update manager I get the following

Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Type 'hpad.net/wfg/0ad/ubuntu' is not known on line 3 in source list /etc/apt/sources.list.d/wfg-0ad-natty.list'


If the Splash window comes up (a new upgrade is available) and I click Upgrade now, nothing happens.

So, how do I upgrade to 11.10?

Thanks

FIXED.

I edited the file and commented out the offending line.

---

