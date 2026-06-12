---
title: "no response from num keys in hardy"
date: 2008-11-24
forum: Philippine Team
---

### Post by Script Warlock on 2008-11-24
this is wierd kc ilang minuto lang wala nang response ang num keys sa keyboard ko except sa enter. at ang + sign naman reacts only to choose or highlight the text..ano kaya to wala naman akong ginalaw sa system is this related to keyboard gconf?...

---

### Post by loell on 2008-11-25
from [https://bugs.launchpad.net/ubuntu/+bug/231173]("https://bugs.launchpad.net/ubuntu/+bug/231173")

try

```
gconftool-2 --set --type=bool /desktop/gnome/accessibility/keyboard/mousekeys_enable 0
```

---

### Post by Script Warlock on 2008-11-25
wow it worked thank very much loell...

lightning fast ang response mo ha...parang medic

---

### Post by loell on 2008-11-25
> **boyet said:**
> lightning fast ang response mo ha...parang medic

kailangan lapatan agad nang first aide google, para di lumala. :lolflag:

---

