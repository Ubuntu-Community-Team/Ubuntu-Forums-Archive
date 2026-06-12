---
title: "orca to run at startup, how?"
date: 2012-05-28
forum: New to Ubuntu
---

### Post by bubazoo on 2012-05-28
how do I get orca to run at startup?

I can run it from a terminal, but it keeps giving me a problem when I do that, and when I close the terminal orca goes bye-bye.

how do I get it to run at startup?

I heard it doesn't work in ubuntu 12.04's unity desktop. then how do I get to gnome-shell then?  don't know how to switch desktops out of unity then

---

### Post by blackbird34 on 2012-05-28
In the gear menu (top right in most Ubuntu Environments) you will find a "Startup Appplications" menu. Orca might be there, if not, First read [this]("http://shuffleos.com/3496/how-to-enable-all-applications-in-startup-applications-ubuntu-11-10/") (same instructions for 12.04) to enable the full list of Startup Applications (many are hidden by default). Orca should show up in that expanded list. Otherwise you can add it to the list: 
Add > 
             Name: Orca ; 
Command: /usr/share/applications/orca

If you want to use gnome-shell, by all means do (see [here]("http://www.unixmen.com/201204-top-things-to-do-after-installing-ubuntu-2/"), instruction number 6) but i have managed to start Orca in Unity myself.

---

### Post by cortman on 2012-05-28
If indeed you decide to use Gnome shell (I love it myself) you can add it to startup by pressing Alt+F2 and typing

```
gnome-session-properties
```

Click the "Add" button, and give the command "Orca". Save and exit.

---

