---
title: "Installing a theme"
date: 2014-05-03
forum: New to Ubuntu
---

### Post by Kraizer on 2014-05-03
I'm attempting to install a new them via the Tweak Tool, and the installation instructions that came with the them asks me to extract the theme into my themes folder. I finally found it, but I cannot move the file from my desktop to the folder; it keeps saying I need root access. How do I get this thing installed? o.o

From what I understand, root is locked by default for security so I don't want to compromise that... I just want a new theme XD

---

### Post by deadflowr on 2014-05-03
Do you have a themes folder in your home folder?
It would be hidden, so ctrl + h to unhide.
(hidden files and folder have adot at the front)

If you don't, then maybe simply create it.
(put the dot at the front, so it knows it's to be hidden folder.)

This will only make the theme available for one user.

To make it available for all users then copy it to the system theme folder
You need to open a terminal(Just look for the program called Terminal)
 and run this
```
sudo cp -R /original/path/of/the/theme/folder /usr/share/themes/
```
sudo gives you root access.
the -R means recursive, so that the contents of the theme folder can also be copied.
Or else it would simply copy an empty folder.

Original path would be something like
```
/home/bob/Downloads/theme
```

Or whatever your path is to where the theme is.

Good Luck

Edit: More on understanding root and sudo in Ubuntu
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

