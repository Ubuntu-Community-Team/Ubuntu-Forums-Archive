---
title: "Install GTK themes?"
date: 2012-06-08
forum: New to Ubuntu
---

### Post by TheDoolster on 2012-06-08
Hi I'm pretty new to Ubuntu but I got to know some advanced stuff pretty quick. I've already installed GNOME 3 shell and the Advanced Settings for Gnome. I downloaded a GTK 3.4 theme and put it in my home/.themes folder, but I can't find it in the GTK themes section of Advanced Settings. I've googled it and used the forum search but nothing helped.

---

### Post by MG&amp;TL on 2012-06-08
> **TheDoolster said:**
> Hi I'm pretty new to Ubuntu but I got to know some advanced stuff pretty quick. I've already installed GNOME 3 shell and the Advanced Settings for Gnome. I downloaded a GTK 3.4 theme and put it in my home/.themes folder, but I can't find it in the GTK themes section of Advanced Settings. I've googled it and used the forum search but nothing helped.

When you say  home/.themes, do you mean /home/.themes or /home/$USER/.themes?

You want to put it in the .themes directory of your homefolder.

---

### Post by TheDoolster on 2012-06-08
I mean /home/User/.themes

---

### Post by MG&amp;TL on 2012-06-08
Hm. Okay, can you post output from a terminal of:

```
ls ~/.themes/
```

(just shows us exactly what's inside).

---

### Post by TheDoolster on 2012-06-08
[COLOR="Red"]**marples-black.tar.gz**[/COLOR]
exactly like that
That's the theme I was going to install

---

### Post by MG&amp;TL on 2012-06-08
Ahah, it's compressed.

Run:

```
tar xvf ~/.themes/[COLOR=Black]marples-black.tar.gz[/COLOR]
```

to decompress, then see if it shows up.

---

### Post by TheDoolster on 2012-06-08
Ok do I have to log off and log on again because it's not there.

---

### Post by MG&amp;TL on 2012-06-08
> **TheDoolster said:**
> Ok do I have to log off and log on again because it's not there.
Oops, I forgot, you need to be in that directory.

```
cd ~/.themes
tar xvf marples-black.tar.gz
```

Sorry!

---

### Post by TheDoolster on 2012-06-08
Thanks a ton, it works now! None of the other tutorials said that. Thanks

---

### Post by MG&amp;TL on 2012-06-08
> **TheDoolster said:**
> Thanks a ton, it works now! None of the other tutorials said that. Thanks

No problem. Rule is, if it's got ".tar." in it, extract it, then stick it in .themes. :)

Have fun.

---

