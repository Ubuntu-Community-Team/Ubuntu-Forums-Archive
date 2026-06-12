---
title: "Error opening Xsane"
date: 2008-06-08
forum: New to Ubuntu
---

### Post by parkinrg on 2008-06-08
Hi , Can anyone help me 
I have recently installed Ubuntu for the first time ( Ver 8.4 )and my Epson 1670 wont work !
When open Xsane and chose my scanner I get the following error message
Failed to open device snapscan :liusb:005:010': invalid argument 
Any ideas ?

---

### Post by parkinrg on 2008-06-08
If anyone is interested , I have just found out that if I reboot my PC and run Windows , then open Epson scanning software , then reboot into Ubuntu , the scanner works perfectly !! If I turn the scanner off and back on , the error re ocurrs !

---

### Post by drs305 on 2008-06-08
The following thread was successful for some people to get their epson scanners to work with xsane:
[http://ubuntuforums.org/showthread.php?t=108256&page=6]("http://ubuntuforums.org/showthread.php?t=108256&page=6")

---

### Post by alienexplorers on 2008-06-08
You need the snapscan 1.4 driver to run your scanner. You can find out more info by going to this page:
[http://snapscan.sourceforge.net/]("http://snapscan.sourceforge.net/")

---

### Post by parkinrg on 2008-06-08
Thanks .I have downlloaded a file esfw30.bin , and need to save it to user/share/sane/snapscan .   but there is not a folder called snapscan . I have tried to make one but it will not let me , also I can not save the file , tried changing the permissions to read write  but no difference.
Ho w do I create folders in the file system and save files ?
Any help would be greatly appreciated

---

### Post by parkinrg on 2008-06-08
.I have downlloaded a file esfw30.bin , and need to save it to user/share/sane/snapscan . but there is not a folder called snapscan . I have tried to make one but it will not let me , also I can not save the file , tried changing the permissions to read write but no difference.
How do I create folders in the file system and save files ?
Any help would be greatly appreciated

---

### Post by drs305 on 2008-06-08
> **parkinrg said:**
> Thanks .I have downlloaded a file esfw30.bin , and need to save it to user/share/sane/snapscan .   but there is not a folder called snapscan . I have tried to make one but it will not let me , also I can not save the file , tried changing the permissions to read write  but no difference.
Ho w do I create folders in the file system and save files ?
Any help would be greatly appreciated

First, you will have to work with the .bin file. Make it executable by either right clicking on the file in nautilus and changing Properties to executable, or in terminal:
```
sudo chmod a+x **path_to_file/esfw30.bin**
```

Open your file manager, find esfw30.bin, and click on it. That will probably create a new folder. Look in the folder and there should be a README or INSTALL file with directions to follow to install the contents.

---

### Post by mikewhatever on 2008-06-08
alt+f2, type gksudo nautilus, now you should be able to create directories and copy files. Changing permissions anywhere in the system tree is not recommended.

---

### Post by sharks on 2008-06-08
or type sudo mkdir usr/share/sane/snapscan

---

