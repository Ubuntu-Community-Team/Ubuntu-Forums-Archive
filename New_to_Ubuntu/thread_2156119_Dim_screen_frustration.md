---
title: "Dim screen frustration"
date: 2013-06-20
forum: New to Ubuntu
---

### Post by edrojas on 2013-06-20
Hello. When I click on the Brightness & Lock icon in the System Settings menu nothing happens, so I can't change change the dim and turning off screen options, and I really want to cange them off because they are driving me mad. I've tried the gconf-editor, xset -dpms, and gsettings commands such as: 

gsettings set org.gnome.desktop.screensaver idle-activation-enabled falsegsettings set org.gnome.desktop.screensaver lock-enabled false

Nothing seems to work, any suggestions?

Thanks.
Ed

---

### Post by monkeybrain2012 on 2013-06-20
What graphic driver do you use? I notice that if you use Nvidia's proprietary driver you can't adjust brightness.

---

