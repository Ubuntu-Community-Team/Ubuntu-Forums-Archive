---
title: "Customizing Thunar Sendto"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by High Camp on 2008-04-29
Hi All

I'm trying to customize my Thunar Sendto menu to be able to create a link to the selected file in /home/user/Common. The purpose of this is to have a folder full of shortcuts to files I commonly work on.

Based on the information contained here:
[http://thunar.xfce.org/pwiki/documentation/sendto_menu](http://thunar.xfce.org/pwiki/documentation/sendto_menu)
[http://help.hardhathosting.com/question.php/95](http://help.hardhathosting.com/question.php/95)

1. I created the folder ./.Local/Share/Thunar/sendto
2. In that folder I created a file called common.desktop
3. In that file I put this:
```
[Desktop Entry]
Version=1.0
Type=Application
Encoding=UTF-8
Name=Common Folder (Create Links)
Exec=ln -s [%f] /home/simon/Common[%f]
Icon=xfprint
```

I also took the example from the above page and created a send to printer menu item and this worked so I know I'm doing most of it right.

Any help would be much appreciated,

---

### Post by High Camp on 2008-04-29
For now I'm right clicking on files and selecting Sendto Desktop (Create Links) and the cutting the file from the desktop and pasting it in the Common folder.

I wish there were a faster and easier way.

---

