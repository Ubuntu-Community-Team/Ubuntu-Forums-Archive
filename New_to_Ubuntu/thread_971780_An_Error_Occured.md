---
title: "An Error Occured"
date: 2008-11-05
forum: New to Ubuntu
---

### Post by govantim on 2008-11-05
E:dpkg was interrupted, you must manually run                               'dpkg--configure-a' to correct the problem.                                 E_cache->open()failed, please report.                                      ??????  I've opened the terminal and typed in the first command, came back saying it's not a valid command. Totally out of my depth here, please help !

---

### Post by taurus on 2008-11-05
You skipped/omitted a couple of spaces.  It should look like this.

```
sudo **dpkg --configure -a**
sudo apt-get update
```

---

### Post by govantim on 2008-11-05
Sorted, thanks taurus.

---

