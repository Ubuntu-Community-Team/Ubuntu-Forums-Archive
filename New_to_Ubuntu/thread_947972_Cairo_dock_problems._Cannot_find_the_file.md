---
title: "Cairo dock problems. Cannot find the file?"
date: 2008-10-14
forum: New to Ubuntu
---

### Post by rockyj on 2008-10-14
Well I just install the .deb version of cairo-dock. Just double clicked the deb file, and it installed. Installed the required plugins directly after. CLicked on my applications/system tools cairo dock. Said something along the lines of "cannot find source". Now I will click on it and it will do nothing at all. Any ideas?

---

### Post by tuxxy on 2008-10-14
Try running it from in a terminal and post the output here, also AWN is a far better dock imo :)

---

### Post by rockyj on 2008-10-14
cairo-dock: error while loading shared libraries: libglitz-glx.so.1: cannot open shared object file: No such file or directory

maybe I will give awn a try really fast

---

### Post by rockyj on 2008-10-14
Now I remember why I am not using AWN. I downloaded AWN, tried to run it and got this message in terminal:
 
/usr/share/avant-window-navigator/awn-manager/awnPreferences.py:242: DeprecationWarning: raising a string exception is deprecated
  raise "\nKey: "+key+" isn't set.\nRestarting AWN usually solves this issue\n"
Traceback (most recent call last):
  File "/usr/bin/awn-manager", line 200, in <module>
    awnmanager = AwnManager()
  File "/usr/bin/awn-manager", line 101, in __init__
    self.prefManager = awnPreferences(self.wTree)
  File "/usr/share/avant-window-navigator/awn-manager/awnPreferences.py", line 150, in __init__
    self.setup_chooser(APP_ACTIVE_PNG, self.wTree.get_widget("activefilechooser"))
  File "/usr/share/avant-window-navigator/awn-manager/awnPreferences.py", line 242, in setup_chooser
    raise "\nKey: "+key+" isn't set.\nRestarting AWN usually solves this issue\n"

Key: /apps/avant-window-navigator/app/active_png isn't set.
Restarting AWN usually solves this issue


Ahh, I am lost

---

### Post by fabounet on 2008-10-15
the message is quite clear, you have to install libglitz-glx
(try to install the dev version too, in case)
then you can launch your dock.

---

