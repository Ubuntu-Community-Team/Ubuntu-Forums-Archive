---
title: "How to change Firefox logo ??"
date: 2008-07-05
forum: New to Ubuntu
---

### Post by Sc4Rzz on 2008-07-05
Hi,

I stumbled upon this SICK looking firefox logo and would like to change it to this one. I found the folder where all icons are stored (/usr/share/pixmaps) but I can't change anything in the folder.. PLEASE HELP 	](*,)

---

### Post by sayakb on 2008-07-05
What icon theme do you use? If it is a pre-installed icon theme, then at a terminal:
```
gksudo nautilus
```Navigate to /usr/share/icon/iconname/scalable/apps
Replace firefox.png there with this one.
Also, do replace the icons of other sizes. (eg: 48x48, 24x24 etc.)

Note: If you are using a custom icon theme that you installed, then open your home folder, press Ctrl+H, goto the **.icons** folder and there, you can find the theme's folder.

EDIT: Sorry, didn't see the attachment before posting. Since you have a .ico file, open it with Gimp and save it as a .png file before you copy it to the above mentioned folder.

---

### Post by nowshining on 2008-07-05
or in the terminal:

 gksudo nautilus /usr/share/icon/iconname/scalable/apps

---

### Post by nowshining on 2008-07-05
or in the terminal:

 gksudo nautilus /usr/share/icon/iconname/scalable/apps

---

