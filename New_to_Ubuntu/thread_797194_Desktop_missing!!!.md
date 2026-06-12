---
title: "Desktop missing!!!"
date: 2008-05-17
forum: New to Ubuntu
---

### Post by kauboy on 2008-05-17
I'm on 8.04, was fine till this boot-up, now my desktop's gone missing!!! Right-click on it does nothing, no icons, no wallpaper, I go to System->Preferences->Appearance and change the wallpaper, theme, no use. My desktop is still unresponsive, shows no icons, no wallpaper, has just a totally black screen with my top and bottom panels and other software fully functional. Just the Desktop that's got zapped by some UFO!!! :(

---

### Post by NightwishFan on 2008-05-17
I believe if you delete the gnome configuration files, it will reset your settings to default, and that might fix it. It should be called something like /home/youruser/.gnome. Rename it to .gnomebackup. You will need to check show hidden files. If you cannot do this from nautilus, then from the command line:
```
mv /home/youruser/.gnome /home/youruser/.gnomebackup
```
Replace "youruser" with your username in the correct context. Reboot and log in and see if it is fixed. If not, to get your settings back, delete the .gnome and rename the .gnomebackup to .gnome

---

### Post by kauboy on 2008-05-17
Yeah, I understand. I'll give it a shot.

---

### Post by kauboy on 2008-05-17
In the hidden files, there's a .gnome2 folder and another .gnome2_private folder but no file by that name. Any clarification?

---

### Post by NightwishFan on 2008-05-17
I believe .gnome2 should be the right one. I am not on gnome so I am shooting in the dark. Kde has a .kde folder so I naturally assumed. Also renaming it is essentially backing it up so you will not break anything.

---

### Post by kauboy on 2008-05-17
Isn't there a more confident and direct way? There must be.

---

### Post by sharks on 2008-05-17
I also had this problem . this helped me:

[http://www.psychocats.net/ubuntu/nonautilusplease](http://www.psychocats.net/ubuntu/nonautilusplease)

---

### Post by NightwishFan on 2008-05-17
None that I know of, I am sorry. I used this method to fix my kde4 yesterday though, so that is why I was pretty sure it would work for you.

The method above might work. Pity gnome is so dependent on nautilus.

---

