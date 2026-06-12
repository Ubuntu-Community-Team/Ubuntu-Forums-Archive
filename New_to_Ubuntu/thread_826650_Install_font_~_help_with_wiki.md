---
title: "Install font ~ help with wiki"
date: 2008-06-12
forum: New to Ubuntu
---

### Post by Andavane on 2008-06-12
Gutsy Gibbon
===================
I am following the wiki
[http://www.wikihow.com/Install-ttf-Fonts-on-Ubuntu]("http://www.wikihow.com/Install-ttf-Fonts-on-Ubuntu")
and read:
"I'm assuming you've already extracted the font to the ~/ directory"
Am not sure exactly what this extracting is.
I want to install georgia.ttf to the myfonts folder.
I have copied it to the desktop. 

Have been using ubuntu for some time, but it is just essays and writing, so am still very dim on the technical side.

Thank you

---

### Post by Bachstelze on 2008-06-12
You can install Georgia (and othe Microsoft fonts) by installing the package *msttcorefonts*. The general procedure for installinf new fonts, though, it to copy it to ~/.fonts if you want it available only for yoursef, or to /usr/share/fonts if you want it available for all users on the system.

---

### Post by billgoldberg on 2008-06-12
> **Andavane said:**
> Gutsy Gibbon
===================
I am following the wiki
[http://www.wikihow.com/Install-ttf-Fonts-on-Ubuntu]("http://www.wikihow.com/Install-ttf-Fonts-on-Ubuntu")
and read:
"I'm assuming you've already extracted the font to the ~/ directory"
Am not sure exactly what this extracting is.
I want to install georgia.ttf to the myfonts folder.
I have copied it to the desktop. 

Have been using ubuntu for some time, but it is just essays and writing, so am still very dim on the technical side.

Thank you

It would be easier to install the microsoft core fonts, that way they will be installed automatically.

Go to system -> administration -> synaptic package manager and search for

msttcorefonts

Install that package and you will be able to use those fonts.

If you download a font, you can install it by copying the font (if it's in an archive right-click it and selec "extract here" first) and then paste it to /usr/share/fonts using the file manager **or** to home/username/.fonts

.fonts is a hidden map in the home folder. Press "ctrl+h" to view it.

---

### Post by Andavane on 2008-06-12
thank you both.
Yes, mst corefonts does work.
I feel the other linux way to do it is much "nicer" but circumstances and all mean there isn't always the time or memory to load all these things into one's schedule.

Oh, by the way:
> **billgoldberg said:**
> .fonts is a hidden map in the home folder. Press "ctrl+h" to view it.
I couldn't see this hidden folder in the home director after holding "ctrl-h" in my home folder the nearest folder is called ".fontconfig".

Regards

John

---

### Post by Kevbert on 2008-06-12
You need to create a new directory called .fonts  In your home directory, in terminal enter
```
mkdir .fonts
```
Any new ttf fonts you can extract to this directory.  To be able to use the fonts immediately, enter
```
sudo fc-cache -fv
```

---

