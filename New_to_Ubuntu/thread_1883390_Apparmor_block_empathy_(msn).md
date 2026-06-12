---
title: "Apparmor block empathy (msn)"
date: 2011-11-19
forum: New to Ubuntu
---

### Post by Frozen Forest on 2011-11-19
Empathy can't login to msn and the reason behind it is that its access is blocked. Is there any workaround?

```


type=1400 audit(1321692363.495:19): apparmor="DENIED" operation="open" parent=1 profile="/usr/lib/telepathy/telepathy-*" name="/etc/default/apport" pid=4523 comm="telepathy-butte" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
type=1400 audit(1321692363.687:20): apparmor="DENIED" operation="open" parent=1 profile="/usr/lib/telepathy/telepathy-*" name="/etc/apt/apt.conf.d/" pid=4523 comm="telepathy-butte" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
type=1400 audit(1321692363.687:21): apparmor="DENIED" operation="open" parent=1 profile="/usr/lib/telepathy/telepathy-*" name="/etc/apt/apt.conf" pid=4523 comm="telepathy-butte" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
type=1400 audit(1321692363.815:22): apparmor="DENIED" operation="open" parent=1 profile="/usr/lib/telepathy/telepathy-*" name="/etc/default/apport" pid=4523 comm="telepathy-butte" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
type=1400 audit(1321692363.815:23): apparmor="DENIED" operation="open" parent=1 profile="/usr/lib/telepathy/telepathy-*" name="/etc/apt/apt.conf.d/" pid=4523 comm="telepathy-butte" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
type=1400 audit(1321692363.815:24): apparmor="DENIED" operation="open" parent=1 profile="/usr/lib/telepathy/telepathy-*" name="/etc/apt/apt.conf" pid=4523 comm="telepathy-butte" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0


```

---

