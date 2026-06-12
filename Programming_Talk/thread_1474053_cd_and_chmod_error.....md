---
title: "cd and chmod error...."
date: 2010-05-05
forum: Programming Talk
---

### Post by Dart00 on 2010-05-05
Im trying to copy some files over with variable names in them based off a script and then chmod them...and well...it doesn't seem to want to work. I think its the quoting but i cant put it all together:


```
gtkWin2Basic=/usr/share/themes/Win2-7Basic

echo "Copying GTK-Themes. Please Wait..."
gksudo 'cp -r gtk-theme/* /usr/share/themes' 
gksudo 'chmod -R 777 '$gtkWin2Basic' '
```And I get this output:

```

# Copying GTK-Themes. Please Wait...
cp: cannot stat `gtk-theme/*': No such file or directorychmod: cannot access `/usr/share/themes/Win2-7Basic': No such file or directory

```Anybody try anything like this before or seen this type of error?

EDIT: I fixed it with this after a lil more research:

gksudo "bash -c 'cp -r gtk-theme/* /usr/share/themes'"

---

### Post by km0r3 on 2010-05-05
> EDIT: I fixed it with this after a lil more research:

gksudo "bash -c 'cp -r gtk-theme/* /usr/share/themes'"

Cool, then mark this thread as Solved. :-)

---

