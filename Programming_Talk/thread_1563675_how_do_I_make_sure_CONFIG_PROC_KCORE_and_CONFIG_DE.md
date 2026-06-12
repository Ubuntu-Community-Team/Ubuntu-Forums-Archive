---
title: "how do I make sure CONFIG_PROC_KCORE and CONFIG_DEBUG_INFO are enabled"
date: 2010-08-29
forum: Programming Talk
---

### Post by jamesbon on 2010-08-29
How do I make sure CONFIG_PROC_KCORE and CONFIG_DEBUG_INFO are enabled 
in running kernel.

---

### Post by Bachstelze on 2010-08-29
```
zcat /proc/config.gz | grep CONFIG_PROC_KCORE
```

/proc/config.gz contains the config of the current kernel.

*EDIT:* Actually, the Ubuntu kernel does not create /proc/config.gz, so

```
grep CONFIG_PROC_KCORE /boot/config-`uname -r`
```

---

### Post by jamesbon on 2010-08-30
Oh great.Thanks.

---

