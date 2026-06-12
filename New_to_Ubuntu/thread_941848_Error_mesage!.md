---
title: "Error mesage!"
date: 2008-10-08
forum: New to Ubuntu
---

### Post by Joshison on 2008-10-08
Keep getting this error message in Ubuntu, hardy.

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
E: _cache->open() failed, please report.

when I was trying to install 3d drivers on my radeon card.  Now I am getting this message when I am attempting to install updates.

---

### Post by philinux on 2008-10-08
Like it says run the command. Just needs sudo though.

```
sudo dpkg --configure -a
```

---

### Post by usererror on 2008-10-08
Something interrupted the setup process.  Did you run

```
sudo dpkg --configure -a
``` yet?

---

### Post by Joshison on 2008-10-08
Yah i tried that and it just asks for my password, then nothing happens.
edit : tried installing new updates and it works now.  Thanks alot guys!

---

