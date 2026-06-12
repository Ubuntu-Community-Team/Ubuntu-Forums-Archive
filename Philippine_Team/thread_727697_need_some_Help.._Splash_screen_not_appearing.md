---
title: "need some Help.. Splash screen not appearing"
date: 2008-03-18
forum: Philippine Team
---

### Post by Pedro0727 on 2008-03-18
I'm using 7.10 Gusty, i'm done installing it, everything work smoothly even my compiz-fusion and other appz. but something wrong with my splash screen is not appearing. but it continued to logIn screen. 

how can i fix it?

---

### Post by wersdaluv on 2008-03-18
> **Pedro0727 said:**
> I'm using 7.10 Gusty, i'm done installing it, everything work smoothly even my compiz-fusion and other appz. but something wrong with my splash screen is not appearing. but it continued to logIn screen. 

how can i fix it?

Gutsy's splash screen is disabled by default. To enable it, 
```
gconftool-2 \
--type bool \
--set /apps/gnome-session/options/show_splash_screen true
```

:KS

---

### Post by raxso on 2008-03-19
you can also install splash screen in the add/remove applications to manage your splash screens....

---

