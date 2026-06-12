---
title: "upgrade from 10.10 to 11.04"
date: 2011-12-31
forum: New to Ubuntu
---

### Post by john009 on 2011-12-31
After 2 or 3 minutes of 'Calculating the upgrade', I receive a message box (with the 'no-entry' sign) stating the following:
-------------------------------------------
Could not determine the upgrade

An unresolvable problem occurred while calculating the upgrade:
The package 'update-manager' is marked for removal but it is in the removal blacklist.

This can be caused by:
* Upgrading to a pre-release version of Ubuntu
* Running the current pre-release version of Ubuntu
* Unofficial software packages not provided by Ubuntu

If none of this applies, then please report this bug against the 'update-manager' package and include the files in /var/log/dist-upgrade/ in the bug report.
---------------------------------------------
Obviously I can't remove the package, as suggested in another thread, as I would then be unable to do an upgrade at all.  I'm also reluctant to remove it from the removal blacklist for the same reason.

To report the bug, I ran 'ubuntu-bug update-manager' in a terminal and received the following message:
----------------------------------------------
The problem cannot be reported:

This is not a genuine Ubuntu package
----------------------------------------------
My original 'Ubuntu' system was Guadalinex, a Spanish customisation of 10.04.  I've since upgraded to Ubuntu 10.10 without problems.

I've removed third party PPAs and the system is fully updated.

---

### Post by grahammechanical on 2011-12-31
As a wild guess you could try using synaptic to re-install the update-manager. See, if that resolves the conflict.

Regards.

---

### Post by ilikelinuxitisthebest on 2011-12-31
remove it from the blacklist. see what happens.

---

### Post by rectec794613 on 2011-12-31
I had this problem too. Most likely you're gonna have to install fresh. Probably a good idea to install 11.10 instead. I doubt a transition from 10.10 to 11.04 would be a smooth one, anyway. You might like starting with a clean slate.

---

### Post by bodhi.zazen on 2011-12-31
> **john009 said:**
> After 2 or 3 minutes of 'Calculating the upgrade', I receive a message box (with the 'no-entry' sign) stating the following:
-------------------------------------------
Could not determine the upgrade

An unresolvable problem occurred while calculating the upgrade:
The package 'update-manager' is marked for removal but it is in the removal blacklist.

This can be caused by:
* Upgrading to a pre-release version of Ubuntu
* Running the current pre-release version of Ubuntu
* Unofficial software packages not provided by Ubuntu

If none of this applies, then please report this bug against the 'update-manager' package and include the files in /var/log/dist-upgrade/ in the bug report.
---------------------------------------------
Obviously I can't remove the package, as suggested in another thread, as I would then be unable to do an upgrade at all.  I'm also reluctant to remove it from the removal blacklist for the same reason.

To report the bug, I ran 'ubuntu-bug update-manager' in a terminal and received the following message:
----------------------------------------------
The problem cannot be reported:

This is not a genuine Ubuntu package
----------------------------------------------
My original 'Ubuntu' system was Guadalinex, a Spanish customisation of 10.04.  I've since upgraded to Ubuntu 10.10 without problems.

I've removed third party PPAs and the system is fully updated.

You will have to remove the offending package, upgrade, and then reinstall the offending package, hopefully to an updated version.

---

