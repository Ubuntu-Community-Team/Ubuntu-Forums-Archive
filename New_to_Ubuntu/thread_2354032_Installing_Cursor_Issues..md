---
title: "Installing Cursor Issues."
date: 2017-02-27
forum: New to Ubuntu
---

### Post by botnerdlen on 2017-02-27
Hey guys, 
so after a good amount of research, I decided to come here. My goal is to install this mouse cursor theme: [https://www.gnome-look.org/content/show.php/OSX+El+Capitan?content=175749](https://www.gnome-look.org/content/show.php/OSX+El+Capitan?content=175749) . But for some reason, every time i save it to the ~/usr/shar/icons folder, it doesn't appear in the Gnome Tweak Tool. I've tried following the README instructions, but I always get this error: cp: cannot stat 'bin/xcursor': No such file or directory


I'm pretty new to Ubuntu and would love any help and knowledge I can get. Thank you all in advanced.

---

### Post by Dennis N on 2017-02-28
> But for some reason, every time i save it to the ~/usr/shar/icons folder, it doesn't appear in the Gnome Tweak Tool.

The location for the cursor folder should be **/usr/share/icons** (your path, **~/usr/share/icons** puts it within your home folder).

---

