---
title: "Can't change directory"
date: 2016-10-16
forum: New to Ubuntu
---

### Post by mermaidman on 2016-10-16
I am using Ubuntu 16.04.  I try to change directories in a terminal to a folder on my laptop but I can only get as far as /home/user/Desktop.  When I try to go from there to a folder on my destop using cd /Folder I get this error message:

bash: cd: /Folder: No such file or directory

---

### Post by deadflowr on 2016-10-16
Try without the /.
like: first
```
cd /home/user/Desktop
```
then
```
cd Folder
```

In fact you can even change to the desktop folder with just
```
cd Desktop
```
or even 
```
cd Desktop/Folder
```
but when you try changing and add the / to it, the system thinks you mean to change into the /Folder directory that doesn't exist.
It thinks that is a directory like /home, or /usr, or /boot. And not a sub-level directory of the Desktop folder.

If that makes sense.

---

### Post by Geoffrey_Arndt on 2016-10-16
when you do "ls" <enter> and then "cd Desktop" <enter>, then, another "ls" . . . what do you see for folders?

---

