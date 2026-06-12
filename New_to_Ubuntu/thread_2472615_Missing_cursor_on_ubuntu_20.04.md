---
title: "Missing cursor on ubuntu 20.04"
date: 2022-03-06
forum: New to Ubuntu
---

### Post by devkwakualdo on 2022-03-06
I am new to ubuntu, I just installed ubuntu 20.04 on an HP pavilion. The cursor was missing throughout the installation, and after logging into gnome, the cursor appears for just a second or two and disappears again. It still works as I can see it highlight stuff when i move my finger on the touchpad. I need help with this issue as it has been frustrating me for days now.

---

### Post by tea for one on 2022-03-06
This is an unusual situation.
Was the cursor missing during your live test session?

If you install gnome-tweaks, you can possibly select an alternative cursor.
```
sudo apt install gnome-tweaks
```
Launch gnome-tweaks > Appearance > Cursor

Temporarily, you can change a hidden setting to allow you to locate the mouse/touchpad pointer.
```
gsettings set org.gnome.desktop.interface locate-pointer false
```
Change false to true
```
gsettings set org.gnome.desktop.interface locate-pointer true
```
Then, press **Ctrl** which will locate the pointer (hopefully).

---

