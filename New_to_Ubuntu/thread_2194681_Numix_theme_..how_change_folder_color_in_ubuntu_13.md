---
title: "Numix theme ..how change folder color in ubuntu 13.10?"
date: 2013-12-19
forum: New to Ubuntu
---

### Post by ChandanIN on 2013-12-19
Hello,


How can I change folder color in ubuntu.
I am using Numix theme.

Any help would be appreciated.

Thank You in advance.

---

### Post by vasa1 on 2013-12-20
I think that Numix is a *gtk* theme and not an *icon* theme. To change the folder color, you'd have to edit the corresponding icon in your icon theme.

---

### Post by Frogs Hair on 2013-12-20
Numix now has  three icon themes and the location is usr/share/icons/numix/places. The  icon color could  be edited using gimp and you would have to change the places/folder content for each icon size included with the set  . You might want to download another set just to experiment with. From what I see in the folder the icon set only offers one folder color with no way to change that from the theme index

---

### Post by vasa1 on 2013-12-20
> **Frogs Hair said:**
> Numix now has  *three icon themes* and the location is usr/share/icons/numix/places. ...
The Numix I mean is the one that came with Xubuntu 13.10. AFAICT, Numix isn't installed by default on Ubuntu 13.10.
```

$ apt-cache search numix
shimmer-themes - Gtk+ themes from Shimmer Project
$
```
and
```
$ ls /usr/share/themes/Numix
gtk-2.0  gtk-3.0  metacity-1  openbox-3  unity  xfwm4
$ 
```
and there's no Numix under /usr/share/icons.

@OP, if you install something from somewhere else, please provide a link to the source.

---

### Post by Frogs Hair on 2013-12-20
Confused , I have the Numix icon theme installed and that is what I thought to OP was referring to the folder color for Numix icons . They are part of the project at the link and 3rd party. [https://launchpad.net/~numix/+archive/ppa/+packages?field.name_filter=icon&field.status_filter=published&field.series_filter=](https://launchpad.net/~numix/+archive/ppa/+packages?field.name_filter=icon&field.status_filter=published&field.series_filter=)

---

### Post by vasa1 on 2013-12-20
> **Frogs Hair said:**
> Confused , ...
Not to worry, I'm sure OP will come back and explain *which* Numix is the subject of the thread :)

---

