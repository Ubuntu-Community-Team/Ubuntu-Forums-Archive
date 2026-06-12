---
title: "wine help.."
date: 2008-06-30
forum: New to Ubuntu
---

### Post by sxytrillian on 2008-06-30
I have installed some windows programs using wine in Ubuntu 8.04.

And i have uninstall ed the programs.

But when i click programs in the wine menu in application its still showing the program which i have installed.

How to remove it totally ? please help me out..

---

### Post by sharks on 2008-06-30
right click on the panel bar at applications and choose edit menus and remove those.

---

### Post by sayakb on 2008-06-30
Maybe its just the shortcuts that are there. 
1. Goto "**~/.wine/drive_c/Program Files**" (.wine is a hidden folder in your Home directory. Press Ctrl+H to display the folder. Inside the **Program Files** folder, delete the program's directory you installed.
2. Goto System->Preferences->Main Menu. Expand** Wine** and then expand **Programs** and delete all entries to the program.

---

### Post by sxytrillian on 2008-06-30
whether unchecking that menu is enough?

---

### Post by sharks on 2008-06-30
yes its enough

---

### Post by sayakb on 2008-06-30
I guess it is not. Wine uninstaller sometimes leaves residual files of the programs it uninstalls. Unchecking the name from the menu will just remove the link to the program, but the residual files would still be there unless you delete them from the **drive_c/program files** folder.

---

### Post by sxytrillian on 2008-06-30
i have deleted the files from  the program file s folder..

Is that enough?

---

