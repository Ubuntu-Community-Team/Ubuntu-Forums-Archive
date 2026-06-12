---
title: "Can't delete folder from trash?"
date: 2008-04-30
forum: New to Ubuntu
---

### Post by rjsec4ever on 2008-04-30
Usually, I get this on Windows. The folder is physically deleted but is still showing up. I add a folder, reboot, and empty it and is fine.

Ubuntu 8.04... different. User and root have two different trashes. If I can't delete the folder, then I must be root. However, there's nothing in root's trash, but my trash!

The newer Nautilus won't let me use the extension to "open as administrator" by right-clicking files/folders. It's installed but is not supported perhaps?

If I delete files as root using Nautilus (via "sudo nautilus" command), it goes into root's trash and not my own.

I'm trying to get rid of one folder and that's all... I need help!

---

### Post by bluefrog on 2008-04-30
in hardy, the trash is now located at ~/.local/share/Trash

if you need to erase something which is in your trash but have a permission problem then you will need to issue the following in a terminal

sudo rm -rf .local/share/Trash/files/*

---

### Post by rjsec4ever on 2008-04-30
:O Woah! Thanks!:KS

---

### Post by pcosta2007 on 2008-06-22
this help me too..thanks a lot!

I was getting this bug too

---

### Post by nhandler on 2008-06-22
> **bluefrog said:**
> in hardy, the trash is now located at ~/.local/share/Trash

if you need to erase something which is in your trash but have a permission problem then you will need to issue the following in a terminal

sudo rm -rf .local/share/Trash/files/*

There is also a ~/.local/share/Trash/info folder. This folder stores 1 info file for every file in the files folder. This info file contains the path of the file (before it was deleted) and the deletion date. If you are trying to remove all traces of a file from your computer, you should be sure to also delete the its file in the info folder.

Also, in nautilus, if you go under Edit->Preferences->Behavior, under the Trash section, there is an option to Include a Delete command which bypasses Trash. This Delete command will appear in your right click menu. It will do exactly what it says, delete a file without sending it to the trash. If you add this option, you won't need to worry about deleting a file from the Trash folder.

---

