---
title: "~/ directory???"
date: 2008-05-21
forum: New to Ubuntu
---

### Post by spotteddog on 2008-05-21
What is the "~/ directory"? And how do I download to "the ~/ directory"?

Thanks

---

### Post by quelx on 2008-05-21
that is an alias for your home directory (/home/username) using that saves you from typing the entire path for instance anywhere on the system you can type ```
 cd ~
``` and you arrive in your home.

---

### Post by NullHead on 2008-05-21
Well your ~/ directory is just a link or shortcut to the current user that you're using in a terminal or in a program. If you type ```
cd ~/
```in your terminal window, then your terminal's active directory will be moved to your home directory, /home/<username>. This is useful for simple bash scripts or just a simple way to get back to your home directory if you're lost or you want to get back quickly, wile using a terminal.

---

### Post by spotteddog on 2008-05-21
Got it! Thanks.  :)

---

### Post by t0p on 2008-05-21
> **NullHead said:**
> Well your ~/ directory is just a link or shortcut to the current user that you're using in a terminal or in a program. If you type ```
cd ~/
```in your terminal window, then your terminal's active directory will be moved to your home directory, /home/<username>. This is useful for simple bash scripts or just a simple way to get back to your home directory if you're lost or you want to get back quickly, wile using a terminal.

This may seem overly tiresome (yawwnnnn) but the simplest way to get back to your home directory is to type

```
cd
```

See that?  No typing "~/" or "send/me/home!!"  Just **cd**  Hehe!! ;)

---

