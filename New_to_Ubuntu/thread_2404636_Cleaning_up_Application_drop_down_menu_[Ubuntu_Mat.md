---
title: "Cleaning up Application drop down menu [Ubuntu Mate]"
date: 2018-10-26
forum: New to Ubuntu
---

### Post by ubuntini2 on 2018-10-26
In Ubuntu Mate 18.04.
Installed a trial version of Nuke but even after uninstalling the  application my drop down menus are filled with broken link icons.
see attached
[https://photos.app.goo.gl/q5D6nZnM2qoALaqg7](https://photos.app.goo.gl/q5D6nZnM2qoALaqg7)

How do I remove these?

---

### Post by DuckHook on 2018-10-26
Please post results of:```
sudo updatedb && locate ".desktop" | grep -i nuke
```
I'm not familiar with this app, so:
[LIST]
[*]How many versions did you install?
[*]It's not in the repos, so how did you install and uninstall? Please describe in detail.
[/LIST]

---

### Post by again? on 2018-10-26
To add to DuckHook's info, Nuke can be installed as root or as a user.
So look for the launchers in **/usr/share/applications** or **~/.local/share/applications**

If Nuke was installed recently and using the file browser to delete, arranging icons by modification date will help find all launchers.

---

