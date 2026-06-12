---
title: "Changing the curser on 12.04, is it possible"
date: 2013-03-11
forum: New to Ubuntu
---

### Post by dougcumiskey123 on 2013-03-11
I am having a proglem with seeing the curser on the screen as a/ its too small for me to see and b/ it goes of the edge and unseen. is it possible to...

a/ make the curser bigger and/or b/ change its colour and make it flash.

Thanks in advance.

---

### Post by siddharth007 on 2013-03-11
Yeah it is possible.You just need to download a tweaker tool for Ubuntu.It is called [Ubuntu Tweaks]("http://ubuntu-tweak.com").With this tool you can do a lot of customizations.Try it.For review follow this [link]("http://bluesteel007india.blogspot.com/2013/03/tweak-your-ubuntu-with-this-smart-tool.html")

---

### Post by stinkeye on 2013-03-11
You can change the size of the cursor using the terminal but does not work consistently in 12.04
eg
**get** current cursor-size (default is 24)...
```
gsettings **get** org.gnome.desktop.interface cursor-size
```

**set** a larger size...
```
gsettings **set** org.gnome.desktop.interface cursor-size 48
```

**reset** to default size...
```
gsettings **reset** org.gnome.desktop.interface cursor-size
```

In 12.10 you also need to create a ~/.Xresources file containing your larger size
eg ```
Xcursor.size:48
```



[B][SIZE=4]However, creating a ~/.Xresources file does not work in 12.04 and the size does not change consistently 
across the desktop.[/SIZE][/B]

You could try this [**_[COLOR="#B22222"]THEME[/COLOR]_**]("http://gnome-look.org/content/show.php/yDmz?content=157167") which highlights the mouse.
[ATTACH=CONFIG]240046[/ATTACH]
Download the theme to ~/Downloads.
Right click on the yDmz.tar.gz archive and extract here.


Move the extracted **yDmz** folder to /usr/share/icons
**the **yDmz** folder must be in ~/Downloads for this command to work.
```
sudo mv Downloads/yDmz /usr/share/icons
```

Then add the cursor theme to the alternatives list
```
sudo update-alternatives --install /usr/share/icons/default/index.theme x-cursor-theme /usr/share/icons/yDmz/cursor.theme 20
```

and choose your added cursor...
```
gsettings set org.gnome.desktop.interface cursor-theme yDmz && sudo update-alternatives --config x-cursor-theme
```
Log out/in

To revert back to the default cursor (DMZ-White)...
```
gsettings reset org.gnome.desktop.interface cursor-theme && sudo update-alternatives --config x-cursor-theme
```

---

### Post by ibjsb4 on 2013-03-11
Another way to do it is install "crystalcursors", its in the software center.  Or in terminal enter:

```
sudo apt-get install crystalcursors
```

Then to choose a new theme:

```
sudo update-alternatives --config x-cursor-theme
```

These cursor themes will be bigger by default and you must log out for changes to take effect.

This works for me in gnome-classic.

---

### Post by Kopkins on 2013-03-11
Something else that might be helpful is if you go to System Settings > Mouse and Touchpad 
You can select the option show position of the pointer when the control key is pressed.

---

### Post by stinkeye on 2013-03-11
> **ibjsb4 said:**
> Another way to do it is install "crystalcursors", its in the software center.  Or in terminal enter:

```
sudo apt-get install crystalcursors
```

Then to choose a new theme:

```
sudo update-alternatives --config x-cursor-theme
```

These cursor themes will be bigger by default and you must log out for changes to take effect.

This works for me in gnome-classic.

Yes, installing a bigger or brighter theme may also be the solution.
Installing and trying cursor-themes from the software centre may be easier as they should be automatically added to the 
 update-alternatives list.

You need to also run one of the tweak tools as well to change the cursor to match  the 
**update-alternatives --config x-cursor-theme** selection.

---

### Post by dougcumiskey123 on 2013-03-15
Thanks: all....

---

