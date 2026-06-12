---
title: "error in update"
date: 2015-01-12
forum: New to Ubuntu
---

### Post by anil8 on 2015-01-12
hi, when i am updating manager or upgrade the sys...... this type issue  occur



An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Could not open file /var/lib/dpkg/status - open (13: Permission denied), E:The package lists or status file could not be parsed or opened.'

---

### Post by Bucky Ball on 2015-01-12
Do you have Software Centre or Synaptic Package Manager or the regular Software Updater GUI open why you are trying to do this? If so, close them.

I'm presuming you're updating/upgrading via the terminal. Are you using:

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

?

---

