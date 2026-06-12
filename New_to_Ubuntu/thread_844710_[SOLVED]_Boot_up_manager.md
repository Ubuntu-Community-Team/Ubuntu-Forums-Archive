---
title: "[SOLVED] Boot up manager"
date: 2008-06-29
forum: New to Ubuntu
---

### Post by gettinoriginal on 2008-06-29
I keep reading about being able to things that load at boot to speed up boot time.  Where does a person look to find what should and should not be booting ??

---

### Post by iaculallad on 2008-06-29
Use SUM instead: It's available in the repo:

```
sudo apt-get install startupmanager
```

EDIT:

> Where does a person look to find what should and should not be booting ??

Navigate to System->Preferences->Sessions, it's under the "Startup Programs" tab.

---

### Post by gettinoriginal on 2008-06-29
I'm sorry, I meant, is there a list somewhere to tell a person what must load and what is optional ??

---

### Post by iaculallad on 2008-06-29
What should load and what should not differs from one system to the other. That means that users can have the option of adding/removing other startup applications using the "Session" (rc.local?).

*Default startup's could be viewed on newly installed Ubuntu setup system when user's had not yet tinkered on settings*

---

