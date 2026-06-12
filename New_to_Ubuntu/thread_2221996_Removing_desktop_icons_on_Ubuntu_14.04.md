---
title: "Removing desktop icons on Ubuntu 14.04"
date: 2014-05-04
forum: New to Ubuntu
---

### Post by renato3 on 2014-05-04
I'm using Ubuntu 14.04 and I would like to know how can I get rid of desktop icons. I already installed Unity Tweak Tools, went to "Desktop Icons" and disabled them all, but they insist on showing. Here is a screenshot:



[IMG]http://s30.postimg.org/46xo0i8bl/Screenshot_from_2014_05_04_18_06_47.png[/IMG]



How do I remove desktop icons???

---

### Post by david98 on 2014-05-04
Usually you just click restore default and the are removed.

---

### Post by deadflowr on 2014-05-04
If the restore to defaults does not work, you can set it in dconf editor.
You can get dconf editor by installing the package dconf-tools.
It's at org > gnome > nautilus > desktop
Uncheck the options for home-icon-visible,network-icon-visible,trash-icon-visible, and volumes-visible.

Or use gsettings from the command line
For home icon
```
gsettings set org.gnome.nautilus.desktop home-icon-visible false
```
for Network
```
gsettings set org.gnome.nautilus.desktop network-icon-visible false
```
for trash
```
gsettings set org.gnome.nautilus.desktop trash-icon-visible false
```
for volumes
```
gsettings set org.gnome.nautilus.desktop volumes-visible false
```

Though, I would expect the tweak-tool to just simply reset them to off, as it should.

---

### Post by renato3 on 2014-05-04
> **david98 said:**
> Usually you just click restore default and the are removed.

I already did, it doesn't work either.

---

### Post by renato3 on 2014-05-04
> **deadflowr said:**
> If the restore to defaults does not work, you can set it in dconf editor.
You can get dconf editor by installing the package dconf-tools.
It's at org > gnome > nautilus > desktop
Uncheck the options for home-icon-visible,network-icon-visible,trash-icon-visible, and volumes-visible.

Or use gsettings from the command line
For home icon
```
gsettings set org.gnome.nautilus.desktop home-icon-visible false
```
for Network
```
gsettings set org.gnome.nautilus.desktop network-icon-visible false
```
for trash
```
gsettings set org.gnome.nautilus.desktop trash-icon-visible false
```
for volumes
```
gsettings set org.gnome.nautilus.desktop volumes-visible false
```

Though, I would expect the tweak-tool to just simply reset them to off, as it should.

They are already set to false:

[IMG]http://s30.postimg.org/45iq3gopt/Screenshot_from_2014_05_04_20_52_54.png[/IMG]

---

### Post by grumblebum2 on 2014-05-04
Do you have nemo installed?
I ask this because in 14.04 I don't have a nautilus setting **computer-icon-visible** but your pic
shows a "Computer" shortcut.

However nemo still has this setting.
Check via terminal...
```
gsettings get org.nemo.desktop show-desktop-icons
```

---

### Post by caver12 on 2014-05-04
> **renato3 said:**
> I'm using Ubuntu 14.04 and I would like to know how can I get rid of desktop icons. I already installed Unity Tweak Tools, went to "Desktop Icons" and disabled them all, but they insist on showing. Here is a screenshot:
How do I remove desktop icons???

Just right click on them and choose Delete. They're gone.

---

### Post by grumblebum2 on 2014-05-04
> **caver12 said:**
> Just right click on them and choose Delete. They're gone.
These icons won't delete in 14.04...don't know if they did previously.

---

### Post by ubuntb2 on 2014-05-31
> **grumblebum2 said:**
> Do you have nemo installed?
I ask this because in 14.04 I don't have a nautilus setting **computer-icon-visible** but your pic
shows a "Computer" shortcut.

However nemo still has this setting.
Check via terminal...
```
gsettings get org.nemo.desktop show-desktop-icons
```

Thanks for this.  I just installed 14.04 as a reload from mint, and could not get rid of that Trash icon no matter what.  Your gsettings clue got me to try this:  
```
gsettings set org.nemo.desktop trash-icon-visible false 
```

I'm not sure why I needed to specify nemo.  I'm using Nautilus and Gnome Flashback with Compiz.  I have nemo, but haven't even used it yet on this new install.  Anyway - thanks.

---

### Post by grumblebum2 on 2014-05-31
nemo must be drawing the desktop then.
Turn off...
```
gsettings set org.nemo.desktop show-desktop-icons false
```

---

### Post by proteanacumen on 2014-06-01
> **ubuntb2 said:**
> Thanks for this.  I just installed 14.04 as a reload from mint, and could not get rid of that Trash icon no matter what.  Your gsettings clue got me to try this:  
```
gsettings set org.nemo.desktop trash-icon-visible false 
```

I'm not sure why I needed to specify nemo.  I'm using Nautilus and Gnome Flashback with Compiz.  I have nemo, but haven't even used it yet on this new install.  Anyway - thanks.


```

~$ gsettings set org.nemo.desktop trash-icon-visible false
~$ gsettings set org.nemo.desktop home-icon-visible false
~$ gsettings set org.nemo.desktop computer-icon-visible false
```

This worked for me too. 
I don't know why I needed to specify nemo either. I am dual-booting with Linux Mint though. Can that have something to do with it?

EDIT 1
to hide mounted volumes from desktop type this: 

```
gsettings set org.nemo.desktop volumes-visible false
```

EDIT 2
It turns out I actually had NEMO installed along side Nautilus (and Dolphin).

---

