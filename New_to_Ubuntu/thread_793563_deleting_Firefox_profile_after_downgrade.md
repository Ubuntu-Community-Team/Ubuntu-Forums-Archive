---
title: "deleting Firefox profile after downgrade?"
date: 2008-05-13
forum: New to Ubuntu
---

### Post by djarcadian on 2008-05-13
I uninstalled Firefox 3 and installed Firefox 2. Now my add-ons aren't working and I suspect it's because I didn't delete my profile. How do I delete my Firefox profiles so I can reinstall my add-ons from scratch?

---

### Post by quelx on 2008-05-13
```
rm -rf ~/.mozilla/firefox/xxxxxxxx.default
```

should remove the profile of course **_be careful_** with rm -rf and the xxxxxxxx should be replaced with the random name on your system.

---

