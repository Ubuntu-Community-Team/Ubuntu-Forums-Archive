---
title: "Problem installing sw, any sw"
date: 2011-10-23
forum: New to Ubuntu
---

### Post by paparoo on 2011-10-23
Ubuntu 11.04

Trying to install Shuter, a screenshot capture program. Per instructions, I 
'sudo apt-get update'.  It partially completes, then ends with an error: 
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

Help!

---

### Post by kaldor on 2011-10-23
This means that another package management program is running. Are you running updates, the Software Centre, or Synaptic? If so, wait for those to finish and close them. Then run the command again.

If for some reason they're running in the background, just do a reboot (for quickness's sake). :)

---

### Post by Old_Grey_Wolf on 2011-10-23
You need to make sure you don't have Software Center and Synaptic open at the same time. If they aren't then you need to remove the lock file with this command ```
sudo rm -f /var/lib/dpkg/lock
```
Then do an update.

---

### Post by paparoo on 2011-10-23
Got it, Two installers open. Thanks for your help, folks.

---

