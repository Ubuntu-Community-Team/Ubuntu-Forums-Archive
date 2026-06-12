---
title: "Accidentally deleted task bar as a start-up process"
date: 2012-11-27
forum: New to Ubuntu
---

### Post by Weboh on 2012-11-27
In an effort to speed up my computer, I ended some start-up processes. Unfortunately, one of those processes was Ubuntu's equivalent to the task bar. Without that, I can't access the "preferences" menu to change it back. I have found out how to use recovery console, so I guess I can use that like terminal to start  the task bar back up. I also might have deleted that process from the start-up processes menu, so I need a command to input into terminal that will put it back permanently, too.
I am using Maverick.

---

### Post by dolphin194 on 2012-11-27
Those two bars that you are calling the "taskbars" are known as Panels in GNOME 2, which is what Ubuntu 10.10 and earlier used.

Found at [http://askubuntu.com/questions/41/resetting-gnome-panel](http://askubuntu.com/questions/41/resetting-gnome-panel)> You can reset the panel by running
  gconftool-2 --recursive-unset /apps/panel   in a Terminal or by hitting Alt+F2 and pasting this command in the  textfield and then hit run. After that gnome-panel needs a restart and  therefore it has to be killed with the command
  pkill gnome-panel   the same way as the command before. The reset gnome-panel will start again automatically. Boot up your computer normally, press Control-Alt-F1 and type those commands in. This will reset both the top and bottom panels back to the defaults. 

I had the same kind of issue before; I accidentally deleted both of my panels in Lucid (10.04)

By the way, Ubuntu 10.10 is no longer updated, so I would recommend going to a newer version.

---

### Post by Weboh on 2012-11-27
It doesn't. It gives me the message "rsp_write()failed: bad file descriptor"

---

