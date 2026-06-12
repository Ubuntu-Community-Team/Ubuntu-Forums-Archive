---
title: "firefox 2?"
date: 2008-10-23
forum: New to Ubuntu
---

### Post by highlyevolved on 2008-10-23
Is there anyway I can revert back to ff2 from ff3?

Cheers

---

### Post by bsharp on 2008-10-23
```
sudo apt-get remove firefox-3.0 && sudo apt-get install firefox-2
```

---

### Post by Mud.Knee.Havoc on 2008-10-23
I recently did that by using the following two commands:

sudo aptitude remove firefox
sudo aptitude install firefox-2

---

