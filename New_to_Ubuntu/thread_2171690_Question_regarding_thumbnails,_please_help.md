---
title: "Question regarding thumbnails, please help"
date: 2013-09-01
forum: New to Ubuntu
---

### Post by jrtarsoly on 2013-09-01
Hello & good day to all,

My question is regarding where does Lubuntu store video & photo thumbnails, how do I acces them, and how can I configure my Lubuntu OS to not store new thumbnails?

I am running Lubuntu AMD64 13.04.

Thank you,
JrT

---

### Post by guy-roussin on 2013-09-01
In a terminal :
rm -rf ~/.thumbnails ; touch ~/.thumbnails

---

### Post by vasa1 on 2013-09-01
> **jrtarsoly said:**
> ...
where does Lubuntu store video & photo thumbnails, how do I acces them, and how can I configure my Lubuntu OS to not store new thumbnails?
...
I think all the official Ubuntu flavors store thumbnails in [FONT=Courier New]~/.thumbnails/large[/FONT] and [FONT=Courier New]~/.thumbnails/normal[/FONT].
If you have dconf editor installed, there are some options in [FONT=Courier New]org.gnome.desktop.thumbnail-cache[/FONT] and [FONT=Courier New]org.gnome.desktop.thumbnailers[/FONT] but I didn't have much luck playing with the settings there with Lubuntu 13.04. So, whenever I remember, I empty the folders from the terminal. Doing it via the file manager could take some time depending on how many images there are. 

By the way, some programs may have their own storage locations for thumbnails or use ~/.cache :)

---

### Post by vasa1 on 2013-09-01
> **guy-roussin said:**
> In a terminal :
rm -rf ~/.thumbnails ; touch ~/.thumbnails
I think there's no need for the second command. I think ~/.thumbnails is one of those things that the system recreates.

---

### Post by jrtarsoly on 2013-09-01
Okay, I can now declare this post as Solved. Thank you so much for your quick responses.

Best of luck,
JrT

---

### Post by ibjsb4 on 2013-09-01
Yes, ~/.thumbnails will recreate if removed.  Like mention dconf has a setting and gconf also has a couple.

dconf editor
[ATTACH=CONFIG]245888[/ATTACH]
gconf editor
[ATTACH=CONFIG]245889[/ATTACH]

EDIT: too late I see :)

---

