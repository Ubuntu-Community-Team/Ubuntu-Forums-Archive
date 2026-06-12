---
title: "Drive Permissions"
date: 2008-10-08
forum: New to Ubuntu
---

### Post by kuproverto on 2008-10-08
Following on from [this]("http://ubuntuforums.org/showthread.php?t=931369") post, I now have access to the drive and can create and delete files and folders but I wanted to ensure I went about it the correct way. Here's what I did:

---

gksudo nautilus

clicked the name of the folder on my second hard drive, backup

right clicked the backup folder and chose Properties

Chose the Permissions tab

In the Others section selected Folder access: Create and delete files
File access: Read and write

I then clicked the Apply Permissions to Enclosed Files button and closed out of all the open windows.

---

Is this correct? 
Is there a much quicker way to do this in the terminal? 
How do I get an icon for the second drive to show up under the places menu?

---

### Post by Ubuntiac on 2008-10-09
Sounds fine.

The faster way in the terminal is 
```
sudo chmod 777 /path/to/your/folder
```

If you want to change the permissions of everything *inside* your folder as well, use:
```
sudo chmod 777 -R /path/to/your/folder
```

---

