---
title: "[SOLVED] sudo through bash script"
date: 2008-06-12
forum: New to Ubuntu
---

### Post by _sphinx_ on 2008-06-12
Actually I was wondering, is there any kind of way to do "su" through bash "script".:popcorn:

---

### Post by decoherence on 2008-06-12
you mean so you aren't prompted to enter a password?

echo yourpassword | sudo -S command

VERY VERY VERY insecure! Probably better to create a password-less user that only has access to what your scripts needs (depending on what it needs)

---

### Post by _sphinx_ on 2008-06-12
I know it's unsecure, but i just wanted it i don't know why. I also read man sudo after your post and found the flag -s. Thanx any ways.

---

### Post by aeiah on 2008-06-12
this is also useful if you're doing a string of commands and want the computer to shut down when they've finished.

```
wget http://this.com/thing.rar && rar -e thing.rar && rm thing.rar && echo yourpassword | sudo shutdown -h now && i can go to bed in peace
```

---

### Post by decoherence on 2008-06-12
heh i like that last command

---

