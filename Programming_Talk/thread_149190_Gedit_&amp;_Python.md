---
title: "Gedit &amp; Python"
date: 2006-03-23
forum: Programming Talk
---

### Post by lee_connell on 2006-03-23
Hey all,

gedit with the pyconsole and shell executor works great for python programming, good job to the guys who put that all together.

One issue I have which would be great to have is to be able to open multiple documents at a time.  I wish I could tell gedit to open a specific folder and any files inside it will open in the editor.

Is there any plugin or something I could do to make this happen?

---

### Post by dragonfyre13 on 2006-03-23
Cant you just ctrl + click them, and select open? Otherwise, I know you can write a sciprt for Nautilus that does it.

---

### Post by lee_connell on 2006-03-23
I tried CTRL + SELECT, that didn't work.  Is there a nautilus script avail?

---

### Post by Wallakoala on 2006-03-23
sorry to hijack the thread, but where did you get the plugin for the pyconsole?
It doesn't seem to be in the repos...

---

### Post by engla on 2006-03-23
[QUOTE=Wallakoala]sorry to hijack the thread, but where did you get the plugin for the pyconsole?
It doesn't seem to be in the repos...[/QUOTE]
It's in the gedit version coming for dapper. So I guess one must install gedit for gnome 2.14 or the whole dapper prerelease.

The upgraded gedit has lots of other cool plugins too, like snippets!

---

### Post by ioslipstream on 2006-03-25
There is no need for a nautilus script.  Just select all the files in the folder, right click, open with "text editor".

---

### Post by dcraven on 2006-03-25
```
gedit /path/to/folder/*
```
That seems to work pretty much as you'd expect.

~djc

---

### Post by dragonfyre13 on 2006-03-27
[QUOTE=dcraven]```
gedit /path/to/folder/*
```
That seems to work pretty much as you'd expect.

~djc[/QUOTE]


Yep, that was pretty much the script.

```

#!/bin/bash
## Just a simple script to open all the .py files in your current directory in nautilus.
## Tim Alexander - Dragonfyre13

gedit "$NAUTILUS_SCRIPT_CURRENT_URI"*.py
```

---

### Post by dragonfyre13 on 2006-03-27
Oh, stick that in here, if you didn't know.

~/.gnome2/nautilus-scripts/

---

