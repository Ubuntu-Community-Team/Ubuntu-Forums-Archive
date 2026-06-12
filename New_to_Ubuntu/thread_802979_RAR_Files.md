---
title: "RAR Files"
date: 2008-05-21
forum: New to Ubuntu
---

### Post by drhvasquez on 2008-05-21
Hi.....

My problem is about to unrar the RAR files...i thought i knew how to do it up today. i got a file that is compressed in 43 rar archives, the problem is that the name of the 43 files are like "How to unrar 01.rar"....so when i entered the command on the terminal unrar x How to unrar 01.rar it said that didn't recognized the file, so i figured out  that if i rename the file and put the name together like "Howtounrar01.rar" it recognized the file and start to unrar the file......the problem is that i dont want to rename the 43 files......

what can i do?

thanks

---

### Post by arsenic23 on 2008-05-21
Well, you could use the gui to open it, or you could rename them all with a single command.

```
rename 's/\ /_/' *.rar
```

Then do your thing. 
If you need to put them back just ```
rename 's/_/\ /' *.rar
```

---

### Post by littletinman on 2008-05-21
ok go into synaptic and type in 


unrar in search


install what shows up

then open the rar file with Archive Manager

This should work

---

### Post by Inxsible on 2008-05-21
Since the names have spaces in them simply use quotes around it.
```
unrar "How to unrar 01.rar"
```

---

### Post by drhvasquez on 2008-05-21
its work with the "commas" but now i get this error....

bushido@U:~/Shared/WWE$ unrar x "WWE_Judgment Day HD 2008-05-18 XviD CD1-SC-SDH.part01.rar"

UNRAR 3.71 beta 1 freeware      Copyright (c) 1993-2007 Alexander Roshal


Extracting from WWE_Judgment Day HD 2008-05-18 XviD CD1-SC-SDH.part01.rar

Creating    WWE Judgment Day HD 2008-05-18 XviD CD1-SC-SDH            OK
Extracting  WWE Judgment Day HD 2008-05-18 XviD CD1-SC-SDH/WWE Judgment Day HD 2008-05-18 XviD CD1-SC-SDH.avi     

Extracting from WWE_Judgment Day HD 2008-05-18 XviD CD1-SC-SDH.part02.rar

...         WWE Judgment Day HD 2008-05-18 XviD CD1-SC-SDH/WWE Judgment Day HD 2008-05-18 XviD CD1-SC-SDH.avi     
Write error in the file WWE Judgment Day HD 2008-05-18 XviD CD1-SC-SDH/WWE Judgment Day HD 2008-05-18 XviD CD1-SC-SDH.avi [R]etry, [A]bort a

Write error in the file WWE Judgment Day HD 2008-05-18 XviD CD1-SC-SDH/WWE Judgment Day HD 2008-05-18 XviD CD1-SC-SDH.avi
Program aborted

am i doing something wrong?

thanks

---

