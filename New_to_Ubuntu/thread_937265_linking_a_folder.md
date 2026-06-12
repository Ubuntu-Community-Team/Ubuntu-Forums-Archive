---
title: "linking a folder"
date: 2008-10-03
forum: New to Ubuntu
---

### Post by canam101 on 2008-10-03
One awkward thing about using nautilus is creating or linking folders. If I open a file containing several folders and want to link one of them to the desktop, I have to right-click and create a link, then left click and drag the link to the desktop.

When I used kde, I could drag the folder to the desktop and see a menu that gave me the choice of moving, copying, or making a link. Under gnome, when I drag a folder somewhere it moves the folder.

And I don't see a way to right-click and create a folder either. I have to create a folder on the desktop and then drag it to the file.

Is there anything I can change to get the flexibility that kde gives in this situation? I looked through the nautilus preferences but don't see anything, but I must be overlooking something.

Thanks.

---

### Post by jamesrl on 2008-10-11
For me in nautilus, I right click on the background of a window, and the first option is to "Create Folder" as is the second option down in Nautilus pull down menu under "File" (with keyboard shortcut [Ctrl]-[Shift]-N

If you want to copy a folder you hold Ctrl as you drag it.  I don't know if there's the functionality to make a link (Ctrl-M) to a folder (aka "shortcut"),  other than to create a link and then move it yourself.  

For moving multiple files/folders at once, you just select the files and folders, press Ctrl-M (to make link) and then all the links will now be selected, and you can move them to the new location.  For a total of one highlight, one keystroke, and one drag to new location.

Anyhow I recommend doing everything from the command line, as I think its much more concise and quicker.  E.g, Make links with "ln -s", move/rename files with mv, copy files with cp, delete (remove) files with rm, and add -r options when you need to descend into subdirectories. etc.

---

