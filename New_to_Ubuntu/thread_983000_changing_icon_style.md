---
title: "changing icon style"
date: 2008-11-15
forum: New to Ubuntu
---

### Post by waffleturd on 2008-11-15
I'm trying to change my icon theme to black-white vista 2.
Here was the instructions.
ReadMe to black-white 2

1.Change your main menu icon
2.different folder icons

1.-add a "Main Menu" to your panel
-run gconf-editor
-navigate to /app/panel/objects
-find a object_x with the "object_type=menu-object".
- tick up "use_custom_icon"
-type in "custom_icon" start-here1, start-here2, ... , start-here11
- if you doesn't like any of this icons you can browse here to an image of your choice

2.In this version I add some different icons for your downloads, documents, music,... folder.
-To use them you must unpack the tar.gz package.
-right click on the folder you wants to change and presspreference
-click on the folder icon and browse to the unpacked black-white2.tar.gz folder and go on to / scalable/places (sometimes /scalable/places/256)
-choose your folder and press open.

However, there is no -find a object_x with the "object_type=menu-object".
in gconf-editor.
Does anyone know where to find it?

---

### Post by fr.theo on 2008-11-15
try this site [http://www.freesoftwaremagazine.com/articles/change_ubuntu_look](http://www.freesoftwaremagazine.com/articles/change_ubuntu_look)

---

