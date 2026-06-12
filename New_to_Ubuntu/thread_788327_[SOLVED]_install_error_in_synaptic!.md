---
title: "[SOLVED] install error in synaptic!"
date: 2008-05-09
forum: New to Ubuntu
---

### Post by kamitsukai on 2008-05-09
I'm trying to install something via synaptic but i just get this error

```
E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory

```

i also get the same error when installing from terminal...

---

### Post by kamitsukai on 2008-05-09
sorted itself out after reboot...

---

### Post by y-lee on 2008-05-09
You can get this error if more than package  manager updating the system through apt (apt-get, synaptic, alien etc...). Be sure No other programs like that are running

From what I've saw on the forums here if any of those programs have crashed you can also get errors like that.

Have you tried rebooting?

If that fails, simply remove the lock file (/var/cache/apt/archives/lock), well, provided you _know_ apt isn't running in any shape or form...

Edit: Ok just saw your last post. Glad it sorted itself out. :)

---

