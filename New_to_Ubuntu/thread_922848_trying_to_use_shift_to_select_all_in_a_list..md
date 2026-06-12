---
title: "trying to use shift to select all in a list."
date: 2008-09-17
forum: New to Ubuntu
---

### Post by fignig on 2008-09-17
i'm trying to use shift so i can select a group of items in a row. but it doesn't seem to be working. where can i find a place to fix this, or how to? 


and btw, i'm trying also go arrange my icons in list form, instead of the icon form that it is in. can anyone help w/ that either?

---

### Post by drs305 on 2008-09-17
Are you using Nautilus? View, View as List.

You can also go into gconf-editor and make list-view the default. Open gconf-editor with this command: gconf-editor  and navigate to the setting seen below, or just run the following:
```

gconftool-2 --type string --set /apps/nautilus/preferences/default_folder_viewer 'list_view'

```

Shift-click is working for me so I can't help with that one.

---

### Post by fignig on 2008-09-17
> **drs305 said:**
> Are you using Nautilus? View, View as List.

You can also go into gconf-editor and make list-view the default. Open gconf-editor with this command: gconf-editor  and navigate to the setting seen below, or just run the following:
```

gconftool-2 --type string --set /apps/nautilus/preferences/default_folder_viewer 'list_view'

```

Shift-click is working for me so I can't help with that one.

ty i got the list view working. i just need the select click working now.

---

### Post by drs305 on 2008-09-17
Just a thought - is the reason you can't shift-click because it opens the folder/file as soon as you click on it? If that is the problem, you can change the action so that a double-click is required to open the file. To change that, Edit, Preferences, Behavior.

If you want to keep it at single-click to open, hold down the shift key before selecting the first file/folder.

---

### Post by fignig on 2008-09-17
nope, that's not the problem i double click to open files, but when i'm selecting files shift click doesn't work. that's when i need it, to select things.

---

### Post by pyromanic123boom on 2008-09-17
It's not shift...it's the control key. Hold it down, and left-click on items to select them.

---

