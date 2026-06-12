---
title: "After adding Ubuntu desktop to Xubuntu..."
date: 2017-07-10
forum: New to Ubuntu
---

### Post by rdb3 on 2017-07-10
I am running Xubuntu 16.04 on a desktop.  It was iso download and created on usb and installed that way.
It runs fine.

I have tried to add an additional desktop, Ubuntu Unity, and did so this way..

sudo apt-get install ubuntu-desktop
sudo apt install ubuntu-session

That went ok, except that I can not get the desktop icons to appear on the desktop.
Copy and pasting them doesn't work.  It's like the desktop won't allow anything to be pasted on it.

Any suggestions.  Thank you.

---

### Post by TheFu on 2017-07-10
Google found this: [https://askubuntu.com/questions/67925/how-to-create-a-desktop-shortcut-in-unity](https://askubuntu.com/questions/67925/how-to-create-a-desktop-shortcut-in-unity)

Unity is going away. Canonical has canceled development and announced they are standardizing on Gnome3 for future releases, so it might not be worth the effort to do anything too complex with Unity at this point.

---

### Post by rdb3 on 2017-07-10
Thanks TF.  I tried the gnome-desktop-item-edit suggestion, but that did not work either.

And I can't drag and drop from anywhere.... icons won't stick.

Also...I can change wallpapers on the desktop via Systems Settings>Appearance just fine, but when I right-click on desktop, nothing appears.

I am working by clicking the icons on the dash.

---

### Post by deadflowr on 2017-07-11
Try enabling the file manager to handle the desktop:
open a terminal and run
```
gsettings set org.gnome.desktop.background show-desktop-icons true
```

---

### Post by rdb3 on 2017-07-11
> **deadflowr said:**
> Try enabling the file manager to handle the desktop:
open a terminal and run
```
gsettings set org.gnome.desktop.background show-desktop-icons true
```

That fixed it.  All the functionality on the desktop is back.  Thanks!!!

---

