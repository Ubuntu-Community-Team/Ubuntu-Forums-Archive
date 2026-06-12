---
title: "[SOLVED] Unable to do dual monitor - help please"
date: 2008-10-11
forum: New to Ubuntu
---

### Post by paker on 2008-10-11
I have an nvidia card. Installed restricted nvidia driver and nvidia-settings. I can get both monitors working by hitting APPLY, but I cannot SAVE. When I try SAVE, error message pops up "unable to create /etc/X11/xorg.conf.backup"

What's wrong?

---

### Post by taqkavar on 2008-10-11
maybe its is a problem of access rights, try running nvidia-settings as root:

sudo nvidia-settings

and do the same thing

---

### Post by paker on 2008-10-11
I am impressed! Thanks.

---

