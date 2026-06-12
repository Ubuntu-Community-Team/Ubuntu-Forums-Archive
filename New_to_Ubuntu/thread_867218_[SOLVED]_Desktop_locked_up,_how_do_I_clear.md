---
title: "[SOLVED] Desktop locked up, how do I clear?"
date: 2008-07-22
forum: New to Ubuntu
---

### Post by garyed on 2008-07-22
Well I was copying & pasting something from the internet to Open office & I'm locked up completely. I can get to tty with Ctrl-Alt-F1 & login but I'd like to know how to restart the desktop without rebooting. Any help appreciated.

---

### Post by jimmy the saint on 2008-07-22
Ctrl-alt-backspace

---

### Post by bhadotia on 2008-07-22
> **garyed said:**
> Well I was copying & pasting something from the internet to Open office & I'm locked up completely. I can get to tty with Ctrl-Alt-F1 & login but I'd like to know how to restart the desktop without rebooting. Any help appreciated.
ctrl+alt+backspace restarts X.

---

### Post by Thingymebob on 2008-07-22
if that doesn't work, from the terminal you can do 
sudo init 1
sudo init 5

to drop you to single user mode (stopping X) and then back to multiuser

---

### Post by garyed on 2008-07-22
Thanks everyone,
Ctrl-alt-backspace worked.
 I figured there was a way to do it without rebooting.

---

