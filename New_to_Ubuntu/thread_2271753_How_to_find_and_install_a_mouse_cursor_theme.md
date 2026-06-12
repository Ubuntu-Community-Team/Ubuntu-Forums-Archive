---
title: "How to find and install a mouse cursor theme?"
date: 2015-04-01
forum: New to Ubuntu
---

### Post by Moonswick on 2015-04-01
Could I have some assistance locating and instaling a large mouse cursor theme, step by step? I'm new to Linux and Ubuntu.

Thanks for the help.

---

### Post by dino99 on 2015-04-01
from 'system settings' top right cog , select the 'mouse' properties
or via dconf (install dconf-editor first)

---

### Post by CantankRus on 2015-04-01
In 14.04 and up, you can increase the size of the default cursor using this terminal command.
```
echo "Xcursor.size:32" > ~/.Xresources && gsettings set com.canonical.Unity.Interface cursor-scale-factor 1.35
```
For an even larger size use....
```
echo "Xcursor.size:48" > ~/.Xresources && gsettings set com.canonical.Unity.Interface cursor-scale-factor 2
```
To set back to default size use...
```
echo "Xcursor.size:24" > ~/.Xresources && gsettings reset com.canonical.Unity.Interface cursor-scale-factor
```
**You need to log out and back in after running any of the previous commands.**

To be able to increase the cursor size, cursor themes must have been created with the different pixel layers.
Not all themes have these layers.
If you want to try different themes you will find some @ [http://gnome-look.org/index.php?xcontentmode=36](http://gnome-look.org/index.php?xcontentmode=36)
To install one of these themes follow [**_[COLOR="#B22222"]THIS GUIDE[/COLOR]_**]("http://ubuntuforums.org/showthread.php?t=2221942&p=13028225#post13028225")

---

