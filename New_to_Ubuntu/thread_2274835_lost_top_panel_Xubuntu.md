---
title: "lost top panel Xubuntu"
date: 2015-04-22
forum: New to Ubuntu
---

### Post by jackobi on 2015-04-22
Hello Everyone.Can anyone help me. I am running Xubuntu 14.04lts on my  laptop but I have removed the top panel by mistake. Can anyone tell me  how to get it back.Thank you in advance for any advice given

---

### Post by zablankinship on 2015-04-22
Right click anywhere on the desktop > Settings > Panel > Plus icon to add a new panel

I believe the default panel has (from left to right):
whisker menu, window buttons, separator, notification area, indicator plugin, clock

---

### Post by nerdtron on 2015-04-22
Go to this directory:
/home/[username]/.config/xfce4/panel

move all it's contents to another folder (just in case, to be safe). Be sure the directory now is empty after moving all contents.

Log-out and log in again. or reboot. Panels should be reset by now.

---

### Post by kerry_s on 2015-04-22
press alt+f3, settings-> panel

just had to give my 2cents

---

