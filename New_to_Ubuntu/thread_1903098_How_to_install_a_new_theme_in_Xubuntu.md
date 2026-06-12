---
title: "How to install a new theme in Xubuntu?"
date: 2012-01-01
forum: New to Ubuntu
---

### Post by hamstermoon on 2012-01-01
Can someone talk me through how do to this?? ](*,) I have downloaded the .tar.br2 file ....

---

### Post by syerges on 2012-01-01
Have you read this?
[https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)

---

### Post by wildmanne39 on 2012-01-01
Deleted

---

### Post by wildmanne39 on 2012-01-01
Deleted

---

### Post by Toz on 2012-01-01
> **hamstermoon said:**
> Can someone talk me through how do to this?? ](*,) I have downloaded the .tar.br2 file ....

Do you mean **tar.b[COLOR="Red"]z[/COLOR]2**?

From a command line:
```
bunzip2 theme.tar.bz2 && tar xvf theme.tar
```
...should uncompress the archive to a folder and associated sub directories.

If you want the theme only available to yourself, then:
```
mkdir ~/.themes
mv theme ~/.themes
```

If you want the theme available to everyone:
```
sudo cp -r theme /usr/share/themes
```

There are two components to an xfce theme - the window manager theme and the appearance theme (located in the xfwm4 and gtkrc-2.0/gtkrc-3.0 subdirectories respsectively). Not all "themes" necessarily come with both components, or as of the last release of xubuntu, with both gtk 2 and gtk 3 components.

To change the window manager (xfwm4) theme, 
*Settings->Settings Manager->Window Manager*

To change the appearance (gtk2/gtk3) theme,
*Settings->Settings Manager->Appearance*

---

