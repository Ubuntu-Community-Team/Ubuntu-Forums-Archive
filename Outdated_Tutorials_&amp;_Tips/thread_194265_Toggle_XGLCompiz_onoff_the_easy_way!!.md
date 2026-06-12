---
title: "Toggle XGL/Compiz on/off the easy way!!"
date: 2006-06-11
forum: Outdated Tutorials &amp; Tips
---

### Post by chollis888 on 2006-06-11
Just doing my part. I came up with this script after days of searching the forums. I took like 8 different threads and rolled them all in to one for this easy Fix. This was written to go along with Poofyhairguy's How-to, Enjoy.

Step 1:

Put this command in the terminal:

```
gedit toggle_compiz.bash 
``` Step 2:
Copy this into the empty file:


```
#!/bin/bash
#
# Checks to see if process "compiz.real" is running.
# If it is, it will kill it.
# If it isn't, it will start it.
#
# By Ubuntu Community

if ps -A | grep -e " compiz.real$" > /dev/null; then
    killall gnome-window-decorator
    metacity --replace &

else
        thefuture
        
fi

``` Step 3:
Now save the file to your home folder. Close gedit. Put this command in the terminal:

```
sudo mv toggle_compiz.bash /usr/bin/

``` Then this:

```
sudo chmod +x /usr/bin/toggle_compiz.bash
``` Then right click on gnome panel and add a shortcut, choose custom launcher in the menu and add:

```
/usr/bin/toggle_compiz.bash

``` in the command field. You can make a desktop launcher by right clicking on the desktop, choosing “create launcher” then use the same command.

Now each time you click on the icon compiz & XGL are toggled on/off! This is essential and its the only way around many bugs.

Note: If you did'nt create a script to lauch XGL/Compiz then replace:

```
 else
        thefuture
``` 
with:
```
else
            gnome-window-decorator &  compiz --replace gconf decoration wobbly fade minimize cube rotate zoom scale move resize place switcher &
```

---

### Post by dabear on 2006-06-11
Probably a nice app, but I preferr this one: [http://www.compiz.net/viewtopic.php?id=1170](http://www.compiz.net/viewtopic.php?id=1170)

---

### Post by gmc on 2006-06-11
Personally I like this, unfortunately I have to make use of it way too much

---

