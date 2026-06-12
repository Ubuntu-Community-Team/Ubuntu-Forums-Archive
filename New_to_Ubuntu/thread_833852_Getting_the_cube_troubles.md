---
title: "Getting the cube troubles"
date: 2008-06-19
forum: New to Ubuntu
---

### Post by Blackicedragoon on 2008-06-19
Hey i am new and i do have my advanced options and the cubes selected but all i get a my one window the flips back and forth like flipping a sheet.

---

### Post by ad_267 on 2008-06-19
In the compizconfig settings manager go to general options then the desktop size tab and set the horizontal virtual size to 4 and the other two options to 1.

---

### Post by Blackicedragoon on 2008-06-19
Great Thanks!

---

### Post by tjwoosta on 2008-06-19
ctrl-alt-leftmousebutton will let you look at the cube from any angle

you can set the zoom and alot of other stuff in the rotate cube section

as for transparency go to general options and the transparency tab

you will need to manuall identify windows to make transparent see attached image

here are some example window identifications

```

type=normal & ! title=Mozilla & ! state=fullscreen & ! title=npviewer & ! title=GNOME & ! title=Google & ! role=gimp-image-window & ! title=Miro & ! name=evince & ! name=opera

```
```

Tooltip | Menu | PopupMenu | DropdownMenu

```

be careful with the opacity value because if you set it too low your windows will disapear (then you have to reboot in safemode to fix)

[IMG]http://i296.photobucket.com/albums/mm186/tjwoosta/ccsm_help.png[/IMG]

---

