---
title: "how to move files"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by rixtr66 on 2008-04-28
im trying to copy a file to adirectory itried to drag and drop and it said i dont have permission.how do i copy the file into the directory?

---

### Post by Barrucadu on 2008-04-28
Where are you trying to move/copy it to? By default you only have write access to your home folder.

---

### Post by tamoneya on 2008-04-28
this is because the directory you are copying to probably requires root partitions.  Hit alt-F2 and type```
gksudo nautilus
```Then drag and drop within the newly started instance of nautilus

---

### Post by elmer_42 on 2008-04-28
If you want a GUI, tamoneya's way is good. However, if a terminal is what you want try this:
```
sudo mv /whatever/directory/or/file /this/is/the/destination
```

---

### Post by stchman on 2008-04-28
> **rixtr66 said:**
> im trying to copy a file to adirectory itried to drag and drop and it said i dont have permission.how do i copy the file into the directory?

You can use the graphical Nautilus via:

```
gksudo nautilus
```

This will allow Nautilus to operate with root privileges.

I prefer to do root stuff via the CLI.

To move a file into a protected area (remember move does exactly that MOVES the file and does not copy it) do this.

```
sudo mv <file to be copied with path> <location>
```

The mv is also the command to rename files.

---

### Post by sasquatch74 on 2008-04-28
Hello and welcome to Ubuntu.  
Let us know exactly what you are trying to do.  What file are you trying to copy?  Why do you want to do this?  From where, and to where are you try to copy the file?
Some files are protected because they are a part of the root system.  Let us know what you want to do and we can help you out.

---

### Post by rixtr66 on 2008-04-28
basically im trying to put a python file into the blender bpydata folder
so i can run indigo.everything is in my home directory.as you can tell im very new to linux i cant even move a file.i can compile and i know how to use alot of software im just not familiar with the linux file system.im running ubuntu 7.10 i chose not to upgrade cause it wont support my wireless im running a laptop,anyway ill try the nautilus thing and let you know,thanks for the help
rixtr:)

---

### Post by rixtr66 on 2008-04-28
thanks,that worked,:)

---

### Post by NT4usB on 2008-04-28
To _move_ files between drives/folders, instead of copying them:
You can highlight a bunch of them (Ctrl+a, Shift+click, Ctrl+click) then click and hold on one of them. 
They will stay selected until you release the mouse.
Drag to another folder will move between folders on the same drive or copy if the destination is on another drive.
In the latter case, holding the Shift key while dragging will move the files instead of copying.

---

### Post by iKant on 2008-05-18
asked a question here but decided to start a new thread sorry for the forum spam :(

---

