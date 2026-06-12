---
title: "permission denied for install  on ubuntu"
date: 2011-09-20
forum: New to Ubuntu
---

### Post by Theking54 on 2011-09-20
i'm logged in as root but i keep getting permission denied 
the main issue is that my internal speakers and headphones play at the same time, when i try this command (/etc/modprobe.d/alsa-base.conf   options snd-hda-intel model=alienware)as suggested i get /etc/modprobe.d/alsa-base.conf permission denied.
please help..am i doing something wrong?

---

### Post by seawolf167 on 2011-09-20
Instead of logging in as root (whose account is disabled by default), use *sudo* while logged in as yourself.

See [RootSudo]("https://help.ubuntu.com/community/RootSudo").

On another note, I recently purchased a new laptop and had the same issue - the solution for me was to install a newer kernel, then it worked flawlessly.

---

