---
title: "Gnome-Do problem"
date: 2008-08-24
forum: New to Ubuntu
---

### Post by Dark006 on 2008-08-24
Hello all, recently I downloaded Gnome-Do and have been using and loving it. The only problem I have with it is that whenever I log off or restart the computer, I have to manually start Gnome-Do again (in other words, Windows Key + Space bar doesn't bring up Gnome-Do). 

Does anyone know of a way to have Gnome-Do automatically started when the computer restarts?

---

### Post by Dark006 on 2008-08-24
Anyone have any ideas?? Its not something I have to add to **/etc/modules** is it? I'm not quite sure what is supposed to be in that file, I just remember having to add ndiswrapper a while back.

---

### Post by dje on 2008-08-24
open system >> preferences >> sessions and add a new startup entry to run this command:
```
gnome-do --quiet
```

dje

---

