---
title: "printing prefencess"
date: 2008-06-19
forum: New to Ubuntu
---

### Post by warrior24 on 2008-06-19
Hi I am having trouble changing printing preferences every time I click on it it opens on the toolbar at the bottom but it then  says opening 0 items then it goes away from the tool bar.

hardy, hp printer 2410 photosmart

---

### Post by UltraMathMan on 2008-06-23
Try starting it via a terminal - if it crashes you'll get more information.
```
/usr/bin/system-config-printer
```

-Hope this helps :)

---

### Post by angryfirelord on 2008-06-23
Since you have an HP, try using HP's GUI instead.
```
sudo apt-get install hp-gui
```
Either find the HP Toolbox icon or run
```
hp-toolbox
```
at the command prompt. If you don't get anything, then you may need to re-run the setup tool:
```
sudo hp-setup
```

---

