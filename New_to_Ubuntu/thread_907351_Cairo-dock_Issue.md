---
title: "Cairo-dock Issue"
date: 2008-09-01
forum: New to Ubuntu
---

### Post by dcruwys on 2008-09-01
ok I installed the cairo dock using the community doc. ([https://help.ubuntu.com/community/CairoDock](https://help.ubuntu.com/community/CairoDock))

I get this error.

uncompressing theme @Cobalt ...
le theme se trouve temporairement dans /home/ostrich/.cairo-dock/themes/@Cobalt
/bin/cp: cannot stat `/home/ostrich/.cairo-dock/themes/@Cobalt/cairo-dock.conf': No such file or directory
find: /home/ostrich/.cairo-dock/themes/@Cobalt: No such file or directory
cp: cannot stat `/home/ostrich/.cairo-dock/themes/@Cobalt/launchers/*.desktop': No such file or directory
find: /home/ostrich/.cairo-dock/themes/@Cobalt: No such file or directory
warning :  (cairo-dock-modules.c:cairo_dock_update_conf_file_with_modules_full:932)  
  No such file or directory
warning :  (cairo-dock-config.c:cairo_dock_read_conf_file:563)  
  Attention : No such file or directory
fDeltaMargin : 0.00 / 50

---

### Post by dcruwys on 2008-09-01
bump

---

### Post by fabounet on 2008-09-02
themes on the server are crushed for the moment, sorry ^_^
I'll upload a new version that can handle these errors tonight, and we'll fix the themes this week.

---

