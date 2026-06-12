---
title: "adding menu entry"
date: 2008-07-06
forum: New to Ubuntu
---

### Post by hammeraxe on 2008-07-06
i just installed the Linux MultiMedia Studio (LMMS) but for some reason it didnt show up in the menu so i wanted to add it manually...
i found LMMS in /usr/bin and created the desktop launcher... still i wanted to add it in the menu as well
sadly the xfce menu editor doesnt allow me to so this as all the program categories are hidden in a "system" entry which cannot be edited
so the question is: how do I add the launcher to my menu?

---

### Post by Elfy on 2008-07-06
I think that you need to make the necessary launcher in /usr/share/applications/ - copy one of the existing desktop files and rename it lmms then you can edit the lmms.desktop to point at lmms

I think you should be able to find and copy a file using these commands

```
ls /usr/share/applications/*.desktop
```
usee one of the filename to replace findfile in the next command

```
sudo cp /usr/share/applications/*findfile.desktop* /usr/share/applications/lmms.desktop
```

To edit the file 

```
gksudo mousepad /usr/share/applications/lmms.desktop
```

Edit the necessary to point at lmms

That should work, although I've not used xubuntu in anger and am going from what I've read and used to help someone edit an existing desktop file

---

