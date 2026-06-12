---
title: "[SOLVED] how do i change the icon in the top left?"
date: 2008-09-25
forum: New to Ubuntu
---

### Post by tjwoosta on 2008-09-25
the title says it 

how do i change this icon?
[IMG]http://i296.photobucket.com/albums/mm186/tjwoosta/Screenshot-1.png[/IMG]

EDIT: i forgot to mention that im using Ubuntu Hardy 64bit

---

### Post by jamesrl on 2008-09-25
Well, it is controlled by the icon settings in the loaded theme, which is set by

System->Preference->Appearance->Theme->Customize Theme->Icons

To create your own icon theme is a little complicated, though there are forums on it.  If you go to [gnome-look.org]("http://gnome-look.org"), you can download/install an icon theme, and then within just replace the icon named start-here.svg with a svg of your choice.

Or if you could just replace (first cp to a backup)
/usr/share/icons/Human/scalable/places/start-here.svg
with your own svg file and reload the icon theme.
E.g., if you have a file ~/new_ubuntu_icon.svg
you can do 
```

sudo cp /usr/share/icons/Human/scalable/places/start-here.svg /usr/share/icons/Human/scalable/places/start-here.svg_original
sudo cp ~/new_ubuntu_icon.svg /usr/share/icons/Human/scalable/places/start-here.svg

```

You also might have to change the places/start-here.xxx in more than 1 place (e.g. change the Human/24x24/places/start-here.png if your panel is ~24 pixels)

---

### Post by tjwoosta on 2008-09-25
thanks

i found it 

/usr/share/icons/Human/24x24/places/start-here.png

---

