---
title: "LightDM or LXDM"
date: 2012-04-01
forum: New to Ubuntu
---

### Post by Foobarz on 2012-04-01
Which one is lighter?

Also, it is very annoying to have to type in the username everytime in lxdm, is there a way to automatically have the username there, but not automatically login?

---

### Post by marinara on 2012-04-01
no idea which is lighter.  I'm using lxdm, and i never have to type in my username.  sorry can't help ya.

---

### Post by Guilden_NL on 2012-04-26
You configure LXDM to automatically login into a sole user account by adding the following with the correct username to etc/xdg/lubuntu/lxdm/lxdm.conf

where bobsyouruncle is the primary user to autologin
```

[base]
autologin=bobsyouruncle

```

---

