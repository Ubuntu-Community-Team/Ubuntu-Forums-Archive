---
title: "Copying side bar address/command!"
date: 2012-10-16
forum: New to Ubuntu
---

### Post by SWGraphics291 on 2012-10-16
When you install Ubuntu 12.04 you get a side bar on the left, they all have the shortcut to the program.

I want to know how to quickly copy the command from them, so say like I could right-click it and it would come up with copy address or something like that!

POST BEEN SOLVED!

---

### Post by nothingspecial on 2012-10-16
You can find the commands that are executed when you click on an icon in it's .desktop file in /usr/share/applications eg

```
$ grep "Exec" /usr/share/applications/firefox.desktop
Exec=firefox %u
Exec=firefox -new-window
$ grep "Exec" /usr/share/applications/thunderbird.desktop 
Exec=thunderbird %u
Exec=thunderbird -compose
Exec=thunderbird -addressbook
```

---

