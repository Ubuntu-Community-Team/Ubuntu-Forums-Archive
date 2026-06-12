---
title: "Change desktop icons"
date: 2014-06-30
forum: New to Ubuntu
---

### Post by wimpy2 on 2014-06-30
I've just installed Lubuntu 14.04. I have a couple of applications on the desktop - a bash script to change the resolution and keyboard and a windows game (spider). I would like to change the icons from the default ones supllied by the OS. I've read a few blogs on this but they all seem to refer to folders and files which I don't have e.g I don't have a /etc/xdg/lxsession/LXDE folder, mine is a /etc/xdg/lxsession/Lubuntu.  Is there any application I can download from the Centre or PPA which would enable me to to this.
I would be grateful for any help or suggestions

---

### Post by Dennis N on 2014-06-30
Create .desktop files for your script and application and place them in your Desktop folder if you want your launchers there. In the desktop files, you can specify the icons of your choice in the Icon= setting. There may already be a .desktop file for your game - if so, you can just change the given Icon path to go to a different icon.

If you are unfamiliar with .desktop files, you would have to learn about those first.

---

### Post by ajgreeny on 2014-06-30
If you right click on one of the desktop icons in Lubuntu you will get the option to open it in leafpad (or is it now mousepad?) which will then be easy to edit as suggested by Dennis N.

Just make sure you use the full pathway to the icon graphic file you want to use.

---

### Post by wimpy2 on 2014-06-30
Thank you both for the replies and advice. Yes,it worked fine. :)

---

