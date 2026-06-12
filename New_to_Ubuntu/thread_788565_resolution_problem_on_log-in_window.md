---
title: "resolution problem on log-in window"
date: 2008-05-09
forum: New to Ubuntu
---

### Post by potterma on 2008-05-09
When I am booting Ubuntu, (Hasty, It was fine under Gutsy), my login screen's resolution is such that the "user name" and "password" fields are not visible on the screen.  Once I log in, the resolution is fine (1600 x 1200).  How do I control the resolution of the login screen?

Thanks in advance!

---

### Post by hotchkikr on 2008-05-09
go into your /etc/X11/xorg.conf file in root (sudo nano /etc/X11/xorg.conf) and delete all the resolutions on that list your monitor doesn't support -> BUT LEAVE THE REST!

This happens when I switch my dirvers to nvidia for some reason...

---

### Post by spiderbatdad on 2008-05-09
I believe the login resolution screen is handled in the file /etc/usplash.conf

---

