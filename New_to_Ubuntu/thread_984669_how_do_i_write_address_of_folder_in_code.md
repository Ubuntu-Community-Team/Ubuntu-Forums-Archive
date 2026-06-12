---
title: "how do i write address of folder in code?"
date: 2008-11-16
forum: New to Ubuntu
---

### Post by Jamiekeese on 2008-11-16
when people type *put destination here* what do i write, its not c:/program files or jamie/desktop or anythuing like that

heeeelp

---

### Post by ciscosurfer on 2008-11-16
It depends on where you are trying to go.  For instance, the "destination" might be a particular directory (folder) where a program/application is located.  What you are referring to is called a "path" (it is called a "path" in Windows as well). Can you provide an example of where you are trying to go, or where someone has told you to go?

If you need to get to your home folder *(**the folder called /home/yourusername, e.g., /home/jamie)*```
cd

***or***

cd /home/jamie
```Let's say you've downloaded something to your Desktop. You would get there by typing the following into a Terminal (the tilda ~ is shorthand for your home folder)```
cd ~/Desktop

***or***

cd /home/jamie/Desktop
```To see what directory/folder you are currently in, you can type the following in a Terminal```
pwd
```To show the contents of a particular directory/folder, you can type the following in a terminal```
ls -lh
```***NOTE: To get to your Terminal, go to Applications > Accessories > Terminal***

---

