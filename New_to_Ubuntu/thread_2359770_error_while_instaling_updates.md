---
title: "error while instaling updates"
date: 2017-04-27
forum: New to Ubuntu
---

### Post by khalilbs on 2017-04-27
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
 
is there any solution ?

---

### Post by Perfect Storm on 2017-04-27
Moved to New to Ubuntu,

---

### Post by deadflowr on 2017-04-27
post the command you ran that gave you the output.

---

### Post by LastDino on 2017-04-27
Often solutions are in front of us
> E: Could not open lock file /var/lib/dpkg/lock - open **(13: Permission denied)**
E: Unable to lock the **administration directory** (/var/lib/dpkg/), **are you root?**

Or at least we are hinted at it

By the time you post the command you used as requested by Deadflowr. This output clearly tells you that command you ran requires root privilege, which you can access by requesting by typing "sudo" in the beginning of the command.

With power comes responsibility, and therefore make sure you know what the command does if you're accessing root privileges.

---

