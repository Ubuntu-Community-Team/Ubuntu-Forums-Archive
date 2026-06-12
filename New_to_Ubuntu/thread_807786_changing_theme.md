---
title: "changing theme"
date: 2008-05-26
forum: New to Ubuntu
---

### Post by Mick8882003 on 2008-05-26
I have managed this before but now I am lost, so what type is a standard ubuntu theme?

beryl ect, I am lost just trying to find a theme!

---

### Post by twright on 2008-05-26
gtk+ or metacity

---

### Post by sayakb on 2008-05-26
Ubuntu by default uses Compiz fusion as a Window manager and GTK as the window decorator. Though you might install emerald as well for beautiful window borders.

---

### Post by Mick8882003 on 2008-05-26
grr i cant install any of these from the theme manager

---

### Post by sayakb on 2008-05-26
Open a terminal and type:
```
sudo apt-get install emerald
```
Then press Alt+F2 and enter:
```
emerald --replace &
```

Now download emerald themes from [www.gnome-look.org](www.gnome-look.org). Goto System->Preferences->Emerald theme manager and Press the Import button to install the theme. Click on the theme to use it.

---

### Post by sayakb on 2008-05-26
Alternatively, to use GTK themes, you do not need emerald. Download GTK themes from [www.gnome-look.org](www.gnome-look.org)
Now goto System->Preferences->Appearance and Drag and drop the GTK theme you downloaded to install it. Just click on the theme to use it.

---

### Post by Mick8882003 on 2008-05-26
Should I need to ativate the other repositorys for hard, just reinstalled it on my comp??

---

### Post by sayakb on 2008-05-26
You need to enable the universe repository for installing emerald. But just enable 'em all and reload your package information.

---

