---
title: "set notepad++ as default text editor for .java/.xls files"
date: 2013-04-15
forum: New to Ubuntu
---

### Post by manjusun on 2013-04-15
Hi All,

I have installed Notepad++ and using it.
How to set Notepad++ as default text editor for .java/.xls  ?

-regards,
Manjunath S

---

### Post by r-senior on 2013-04-15
Right click on a .java file in the file manager (Nautilus), go to "Properties" and the "Open With" tab. Set the default application to your choice. 

Repeat for .xls files.

---

### Post by manjusun on 2013-04-15
Found it,

needed one line addition for file /etc/gnome/defaults.list
  text/java=Notepad++.desktop

and now able to open .java files with Notepad++

---

