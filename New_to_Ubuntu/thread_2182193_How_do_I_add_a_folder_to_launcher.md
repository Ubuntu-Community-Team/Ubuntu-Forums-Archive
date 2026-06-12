---
title: "How do I add a folder to launcher?"
date: 2013-10-20
forum: New to Ubuntu
---

### Post by nsPn3K7 on 2013-10-20
Hi. I have just started using Ubuntu 12.04. I am a total newbie.

I would like to add the 'Downloads' folder that is located in Home to the launcher that appears on the left side. How do I do that? Drag & Drop does not seem to work.

Thanks!

---

### Post by rihikz on 2013-10-20
Hello. 
Currently you can only pin applications. A folder isnt an application. There are ways to modify it to do this.
Check this [http://askubuntu.com/questions/125842/how-to-add-folder-or-file-to-launcher](http://askubuntu.com/questions/125842/how-to-add-folder-or-file-to-launcher) out and look up your question on google. 
Im sure you wil find a way to do it.

---

### Post by mansonfan78 on 2013-10-20
Create a launcher with this as the command:  [Exec=nautilus --no-desktop % /path/to/folder]   (exclude the brackets). The "--no-desktop" parameter may not be necessary, but it helps avoid some potential problems with nautilus taking over the desktop.

---

### Post by newb85 on 2013-10-20
You may already know this, but you *can* right-click the Files icon (the first icon below the Dash icon) and select Downloads from there.

---

### Post by deadflowr on 2013-10-20
> **newb85 said:**
> You may already know this, but you *can* right-click the Files icon (the first icon below the Dash icon) and select Downloads from there.

Quicklists for the win!

You can also use the keyboard to navigate as well.
alt + F1 and then using the arrow keys to move up and down and right arrow left arrow move to the quicklist selections.
press enter to open, as usual.

---

### Post by Jonathan Precise on 2013-10-20
Try:

```
gnome-desktop-item-edit --create-new /home/$USER/Desktop/
```

from a command-line **<Ctrl+Alt+T>**

For the command put in:

> ```
nautilus **/path/to/the/folder**
```

Replace **/path/to/the/folder** with the complete path to the folder.

Choose any icon.

Drag this to the launcher. DONE!!!

---

