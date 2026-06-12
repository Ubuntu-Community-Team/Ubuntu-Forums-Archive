---
title: "How to make graphical shortcuts similar to .desktop files"
date: 2020-08-23
forum: New to Ubuntu
---

### Post by jcdenton1995 on 2020-08-23
Hello everyone,

Is there a way to make graphical shortcuts, similar to .desktop files, but that can be placed in any directory?

I suppose it's not really a shortcut that I need but rather a file with an icon that runs a specific command when double clicked. I'd thought about just making a symbolic link but that wouldn't be the same thing I don't think?

---

### Post by Holger_Gehrke on 2020-08-23
Have you tried using a .desktop file ? At least on XUbuntu in Thunar .desktop file are treated the same everywhere, so for me they are just what you describe ...

Holger

---

### Post by CatKiller on 2020-08-23
> **jcdenton1995 said:**
> Hello everyone,

Is there a way to make graphical shortcuts, similar to .desktop files, but that can be placed in any directory?

I suppose it's not really a shortcut that I need but rather a file with an icon that runs a specific command when double clicked. I'd thought about just making a symbolic link but that wouldn't be the same thing I don't think?
That would be a .desktop file. They don't have to go on the desktop. Launchers, menu entries, and items on the panel are .desktop files. 

Not being able to launch things from a .desktop file through a file manager isn't because of their location, it's because the Gnome devs took that ability out of Nautilus. You can use a different file manager. 

You're right that symbolic links are something else entirely.

---

### Post by drpjkurian on 2020-08-27
Hi
I use the menu editor to create a launcher.

---

### Post by ActionParsnip on 2020-08-27
Is it a file you want to make accessing a file easier or is it an actual icon that you want to be able to double click ?

---

### Post by TheFu on 2020-08-27
> **jcdenton1995 said:**
>  Is there a way to make graphical shortcuts, similar to .desktop files, but that can be placed in any directory?

I suppose it's not really a shortcut that I need but rather a file with an icon that runs a specific command when double clicked. I'd thought about just making a symbolic link but that wouldn't be the same thing I don't think?

For  "A", create the file using any editor.
For "B", use the **ln -s** command. Some file managers can create symlinks too.

I've never had any use for a .desktop file, but used symbolic links about 50x a day. One is only useful for specific GUI programs and the other is part of the file system, available to all programs for use. Symlinks work on servers. .desktop files are useless on a server.

---

