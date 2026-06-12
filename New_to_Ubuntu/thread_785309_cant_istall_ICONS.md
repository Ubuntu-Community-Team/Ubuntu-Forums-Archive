---
title: "cant istall ICONS???"
date: 2008-05-07
forum: New to Ubuntu
---

### Post by malaya on 2008-05-07
- huhu, please help me.. i cant install the icons that i downloaded in the gnome-look.org.. please help me.

---

### Post by NewDisciple on 2008-05-07
System - Preferences - Appearance then on the bottom of window - install.  Go to location of download and select.

---

### Post by Joeb454 on 2008-05-07
I think you can also drag and drop the file into that window :)

---

### Post by munkyeetr on 2008-05-07
1) Open a terminal window (**Applications** -> **Accessories** -> **Terminal**)
2) **cd** into the directory where your downloaded icon theme is stored.
3) Run the following (substitute the name of the icon archive for **icons**)
```

sudo tar xvf **icons**.tar /usr/share/icons

```
4) **System** -> **Preferences** -> **Appearance**
5) Press the **Customize...** button
6) On the **Icons** tab, choose the theme you just installed
7) Close all the dialogs.

---

### Post by malaya on 2008-05-07
> **munkyeetr said:**
> 1) Open a terminal window (**Applications** -> **Accessories** -> **Terminal**)
2) **cd** into the directory where your downloaded icon theme is stored.
3) Run the following (substitute the name of the icon archive for **icons**)
```

sudo tar xvf **icons**.tar /usr/share/icons

```
4) **System** -> **Preferences** -> **Appearance**
5) Press the **Customize...** button
6) On the **Icons** tab, choose the theme you just installed
7) Close all the dialogs.

- this wont work. the downloaded icons are in a zip format.

---

### Post by TeoBigusGeekus on 2008-05-07
Extract the .zip file on your Desktop. 
If its content is a .tar.gz or a tar.bz2 file, just drag and drop it into the Themes tab of the Appearance dialog box.

---

### Post by studo77 on 2008-05-07
Or you could install Art Manager. It is an easy to use program for installing the various themes, icons and so on.

---

### Post by Nano Geek on 2008-05-07
Where did you download those icons?

---

### Post by NilsE on 2008-05-07
An alternative is to open nautilus with gksudo in a terminal 

gksudo nautilus

browse to the location of the archive file, open it up and extract all to /user/share/icons with the create folders option clicked on. Then you will see it in Appearance.

---

