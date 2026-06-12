---
title: "How do I add a folder shortcut to the Launcher?"
date: 2014-01-22
forum: New to Ubuntu
---

### Post by dave_h2 on 2014-01-22
I've tried dragging and dropping, right-clicking, web searching, but I can't find the way to add a folder shortcut to the launcher. Specifically I want to add a Pictures folder shortcut.

---

### Post by monkeybrain20122 on 2014-01-22
You need to create a .desktop file for the action. You can do this by simply modifying the .desktop file for "Files" on the launcher, in the terminal

```
gksudo gedit /usr/share/applications/nautilus.desktop
```

Change Name to something else, like Name=Pictures
and change the line Exec=...
to
Exec=nautilus /home/username/Pictures
"usernname" is your username
Then save it as something like 
openpicture.desktop

Now open the dash and type Pictures and you should see an icon like Files but called "Pictures", drag and drop it to the launcher.

---

