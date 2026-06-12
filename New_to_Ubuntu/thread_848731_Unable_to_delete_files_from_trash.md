---
title: "Unable to delete files from trash"
date: 2008-07-03
forum: New to Ubuntu
---

### Post by MaPeD on 2008-07-03
Hi

For some reason im unable to delete some files from the trash bin... I have 4 folders in there with the same name and its only these 4 i cant delete..

is there a command to clean the bin from terminal?

thanks in advance

---

### Post by Claus7 on 2008-07-03
Hello,

```
cd .Trash
sudo rm -rf *.*
```

EDIT: Watch out this command! If you do it in the wrong directory it will erase everything that this folder contains! And without asking you whether you are sure or not.

Regards!

---

### Post by sisco311 on 2008-07-03
The Trash folder is a hidden folder(the folders name begins with a period) in your home directory. You can press Ctrl+H in nautilus or select Show Hidden Folder from the View menu to list the hidden folders.

You can open nautilus as root in the .Trash folder:
     ```
gksu nautilus ~/.Trash
```      
in Hardy Heron the Trash is in ~/.local/share/Trash/files/
     ```
gksu nautilus ~/.local/share/Trash/files/
```      
You can delete the content of the folder as root from the terminal:
     Code:```
sudo rm -fr ~/.Trash/*
```      
Hardy Heron:
     Code:```
sudo rm -fr ~/.local/share/Trash/files/*
```

---

### Post by sisco311 on 2008-07-03
> **Claus7 said:**
> Hello,

```
cd .Trash
sudo rm -rf *.*
```EDIT: Watch out this command! If you do it in the wrong directory it will erase everything that this folder contains! And without asking you whether you are sure or not.

Regards!
the trash folder in Hardy is ~/.local/share/Trash/files/
If somebody ignores the *bash: cd: ./.Trash: No such file or directory* warning,
then the rm command can be very dangerous.

---

### Post by MaPeD on 2008-07-03
well opening the trash bin as root did something bad
it ate all my RAM and half of swap file..
had to hit reset button coz system had stopped responding

---

