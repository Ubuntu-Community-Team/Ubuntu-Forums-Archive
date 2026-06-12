---
title: "[SOLVED] I have no network manager icon"
date: 2008-06-06
forum: New to Ubuntu
---

### Post by captgadget on 2008-06-06
and I have no option when I right mouse click on the panel to add anything. What did I do wrong here?

---

### Post by sam_delta on 2008-06-06
do you have the taskbar (notification area) on the top right? if not, you can add it by right click the panel and click on add "notification area" , if you have the taskbar, but not the network manager, make sure you have it installed by typing
```
 sudo apt-get install network-manager network-manager-gnome
```

sam

---

### Post by RomeReactor on 2008-06-06
Hi. If you already had Network Manager installed (or you installed it following the command in the previous post) and you still can't see the icon in the top panel, make sure it's running by pressing ALT+F2 and write or paste:
```
nm-applet --sm-disable
```

then press ENTER. If this brings it back, then that's all there's to it; usually, if not always, when you restart the panels the Network Manager icon doesn't show up.

If this still doesn't help, you may be missing the notification area. Right-click on the top panel, choose "Add to Panel..." and double click on "Notification Area".

---

### Post by ispy on 2008-06-21
thank you thank you thank you thank you!!!!!!

i've been trying to fix that for EVER!!!!!

I love you guys.

:guitar:

---

