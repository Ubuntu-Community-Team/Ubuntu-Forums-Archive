---
title: "Notebook w/ lubuntu doesn't start."
date: 2016-03-15
forum: New to Ubuntu
---

### Post by luiz_carlos2 on 2016-03-15
Hey guyss, help me out, I'm new at Linux.
I do not know what happened and neither the cause.
How to proceed?

---

### Post by sandyd on 2016-03-15
You have major filesystem corruption. May be bad disk, may be just corruption caused by loss of power, improper shutdown/etc

We can check the hard disk health first.
Boot into a LiveCD, and run
```

sudo apt-get install smartmontools
sudo smartctl -t short /dev/sda
# Wait a few minutes
sudo smartctl --all /dev/sda

```

---

