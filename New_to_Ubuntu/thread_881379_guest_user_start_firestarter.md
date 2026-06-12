---
title: "guest user start firestarter"
date: 2008-08-05
forum: New to Ubuntu
---

### Post by animalprimate on 2008-08-05
I have a guest user now for "every day use", for more secureness:)

I understand Firestarter is still working for me but I would like to watch the tray icon so I can see when I'm hit.  but guest user doesn't have access to sudo and cant start up Firestarter, does anyone know how to allow Guest Users to start Firestarter app?:confused:

---

### Post by tuxxy on 2008-08-05
I think firestarter has stopped development now, you should use ufw

[https://wiki.ubuntu.com/UbuntuFirewall](https://wiki.ubuntu.com/UbuntuFirewall)

---

### Post by brian_p on 2008-08-06
> **animalprimate said:**
> 

I understand Firestarter is still working for me but I would like to watch the tray icon so I can see when I'm hit.  but guest user doesn't have access to sudo and cant start up Firestarter, does anyone know how to allow Guest Users to start Firestarter app?:confused:

```
man sudoers
```

and

[https://help.ubuntu.com/community/Sudoers](https://help.ubuntu.com/community/Sudoers)

---

