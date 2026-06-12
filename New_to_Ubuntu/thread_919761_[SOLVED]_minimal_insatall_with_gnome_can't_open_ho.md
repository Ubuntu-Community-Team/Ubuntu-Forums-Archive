---
title: "[SOLVED] minimal insatall with gnome can't open home from places"
date: 2008-09-14
forum: New to Ubuntu
---

### Post by iansane on 2008-09-14
Hi, I tried a minimal install to be able to install specific packages when I want them.

I installed the following.

xorg
gdm
nautilus
nvidia-glx-new
jockey
gnome-core
gnome-system-tools
gnome-app-install

It loads up fine but cd wouldn't auto mount so I installed gnome-volume-manager.

Still wouldn't work so I went to look for start up script in home and found out I can't open home, computer, filesystem, or anything from the places menu.

Do I need to add another package?

Thanks

---

### Post by iansane on 2008-09-14
Sorry!!

Apparently gnome-volume-manager needed a restart. I didn't think it would effect me going to places on the menu but it did cause after restart everything seems to be fine.

I should have restarted anyway before posting.

---

