---
title: "changing permissions"
date: 2008-08-09
forum: New to Ubuntu
---

### Post by Randicvs Andersonvs on 2008-08-09
I cannot convince Ubuntu I am the owner of my computer. I need guidance to change the permissions. I tried a command prompt I found in the fora, but it did not work. (I am not a programmer, so I need command prompts to have every mark and space listed.)I would appreciate any help that is offered. 
Please forgive my my computer incompetence.

---

### Post by starcannon on 2008-08-09
Press:
Alt-F2

then enter in the text box:

gksu nautilus

now you have a file browser opened with "admin" powers.
***_[COLOR="Red"][SIZE="4"]BE VERY CAREFUL![/SIZE][/COLOR]_***
You now have god mode enabled, you can hose your system without meaning to, that said browse to the folder, file, script, or program that you want to change the permissions on, and:

Right Click it
Choose Properties
Choose Permissions
Choose from the dropdown menus the appropriate users, permissions, etc... close, the dialog box
Close the admin nautilus(file browser) window(close all file browsers to be certain)

You should now have the item YOU modified, set to the permissions YOU specified.

---

### Post by Randicvs Andersonvs on 2008-08-09
Thank you for the help, oh knowledgable one.

---

