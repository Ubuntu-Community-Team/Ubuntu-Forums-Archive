---
title: "Openbox: Set autologin using sddm.conf file."
date: 2021-12-30
forum: New to Ubuntu
---

### Post by antonio-cpr on 2021-12-30
Hi!
I'm using Lubuntu 21.10 and I would like to set autologin but using Openbox instead of LXQT DE. How can I do that?

I tried the following setting but did not work.
```
[Autologin]
User=claudio
Session=Openbox
```

---

### Post by GhX6GZMB on 2021-12-30
Where is your sddm.conf file placed?

---

### Post by antonio-cpr on 2021-12-31
> **ml9104 said:**
> Where is your sddm.conf file placed?

By default:
```
/etc/sddm.conf
```

At the moment here it's content:
```
[Autologin]
Session=Lubuntu
```

---

