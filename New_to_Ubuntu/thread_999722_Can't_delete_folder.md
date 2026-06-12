---
title: "Can't delete folder"
date: 2008-12-02
forum: New to Ubuntu
---

### Post by Maringouin on 2008-12-02
I tried to install a free programme called Compendium (see [http://compendium.open.ac.uk/institute/](http://compendium.open.ac.uk/institute/))

Compendium comes in a tarball. When I unpacked it (tar -xvzf [package]). I got a folder on which I can get no permissions at all to either go into it, move it, or delete it. The permissions given are:

Owner : 503 / Folder access : Create and delete files / File access : --- 
Group : 503 / Folder access : None / File access : ---
Other :     / Folder access : None / File access : ---

I have no idea who or what '503' is.

The folder is just sitting there in my wastebasket. How do I get rid of it?

I'm a complete and utter newbie but can follow clear instructions. Thanks for your help!

---

### Post by drs305 on 2008-12-02
If you are sure you want to delete it, open nautilus with admin rights:
```
gksudo nautilus
```
You use 'gksudo' because you are opening a gui-based app.

Browse to the folder and delete it. Use SHIFT-DEL to permanently delete it otherwise it will end up as a file owned by root in the trash bin. This can get to be a problem.

For more information about why a normal user can't delete certain trash items, refer to:
[Disk Full? Check Your Trash Bin]("http://ubuntuforums.org/showthread.php?t=898573")

---

### Post by bmwman on 2008-12-02
Open up Nautilus as Root and you'll be able to delete anything you want or empty your trash. In a Terminal type > sudo nautilusand then enter your password. Carefull what you're deleting .

;)

---

