---
title: "Changing themes and folder colors in 16.04 LTS with Unity"
date: 2018-04-03
forum: New to Ubuntu
---

### Post by waltd on 2018-04-03
Hi all, I'm new to Ubuntu. I have version 16.04 LTS with Unity running on a System76 laptop. How can I change themes, especially folder colors?  Thank you for your support.

---

### Post by Frogs Hair on 2018-04-03
Start with Appearance Settings and if you want to add 3rd party themes see the following.  Downoload the correct GTK theme version for your Ubuntu release  [https://www.gnome-look.org](https://www.gnome-look.org)

Fully extract the theme packages and hold the folders on the desktop until needed . (Right Click Package > Extract Here) 

Install Unity Tweak Tool

(Single User) Create a .themes and .icons folder in home / hidden folders . Use Crtl + H to open hidden folders in the Nautilus file browser.

(All Users) Use gksudo or sudo -H nautilus in the terminal to open the Nautilus as root and navigate to > File System or Computer/ usr / share / themes or icons . Move theme/icon folders into desired location. Use the Unity Tweak Tool to make theme and icon selections.

---

