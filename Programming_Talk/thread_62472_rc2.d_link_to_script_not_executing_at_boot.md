---
title: "rc2.d link to script not executing at boot"
date: 2005-09-04
forum: Programming Talk
---

### Post by professor_chaos on 2005-09-04
Wasn't getting any help posting this in the application section, so I'll try here.
I'm trying to execute a programme at boot, with a script linked to /etc/rc2.d

My script /etc/init.d/script is...


```

#!/bin/sh test -x /path2binary/binary || exit 0 hostn=`hostname` binary -a $hostn
```



I have correctly set the symlink as

```

/etc/rc2.d/S20script -> ../init.d/script
```



I can execute is fine as

```
/etc/rc2.d/S20script
```


It just doesn't start at boot. Arrgh!!!

I would be much appreciative of any help. Thank you in advance.

---

### Post by evilghost on 2005-09-04
sudo chmod 755 /etc/init.d/script
sudo update-rc.d script defaults

---

### Post by professor_chaos on 2005-09-04
damn it. I'm so stupid. The path to this program isn't declared until /etc/bash.bashrc and I didn't specify the full path in the script.

I should know better. Always with full path (I say to myself while I bang my head against table).

---

