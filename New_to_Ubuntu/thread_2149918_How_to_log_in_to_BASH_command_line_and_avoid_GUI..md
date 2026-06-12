---
title: "How to log in to BASH command line and avoid GUI."
date: 2013-05-30
forum: New to Ubuntu
---

### Post by peterdac on 2013-05-30
How to log in to BASH command line and avoid GUI.  I'm using "Beginning Ubuntu Linux" third edition, Apress, and the page #312 refers to a file GDM and a short cut "/etc/rc3.d/S13GDM".  However, the search tools don't find either directory or file in both versions 8.04 Hardy Heron LTS and 12.04 Precise Pangolin LTS. Clearly the authors data was not updated to the publisher's final print run.  Can anyone bring me up-to-date?

---

### Post by prodigy_ on 2013-05-30
Ubuntu doesn't use GDM anymore. If you simply want to switch to a text console, press Ctrl+Alt+F1 (works with any Fx key up to F6) and log on with your username and password. Password won't echo on the display in any way - this is normal.

If you want to stop GUI from loading at system startup:
[http://askubuntu.com/questions/196603/how-to-remove-the-graphical-user-interface](http://askubuntu.com/questions/196603/how-to-remove-the-graphical-user-interface)

If you want to remove GUI completely:
[http://askubuntu.com/questions/6302/how-can-you-remove-unity](http://askubuntu.com/questions/6302/how-can-you-remove-unity)

---

### Post by HiImTye on 2013-06-01
ctrl+alt+f1 ;)
ctrl+alt+f7 to return to LightDM or your desktop
[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]

---

### Post by Cheesemill on 2013-06-01
To always boot into CLI mode run the following command...
```
echo "manual" | sudo tee -a /etc/init/lightdm.override
```

Once you are logged in you can start the GUI by running...
```
startx
```

---

