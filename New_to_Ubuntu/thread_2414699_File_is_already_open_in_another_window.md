---
title: "File is already open in another window"
date: 2019-03-14
forum: New to Ubuntu
---

### Post by zak100 on 2019-03-14
Hi,
I am trying to open a text file in Ubuntu. I am getting the message file is already opened in another window. Somebody please guide me how to close other instances of opened file.

Zulfi.

---

### Post by deadflowr on 2019-03-14
Try cycling through your open windows with alt + tab.

---

### Post by Holger_Gehrke on 2019-03-14
'lsof' on the command line will give you a list of all currently opened files. Search that list for the name of the file you want to open like so
```
lsof|grep 'the name of you file'
```
The first column of the output is the name of the program.

Holger

---

### Post by jdeca57 on 2019-03-14
All good advice but to keep it very simple log out. And then log in and all previous activity is gone.

---

### Post by zak100 on 2019-03-15
Hi Everybody, Right now i just tried the solution provided by jdeca57and it worked.

I woud try other solutions  soon.

Zulfi.

---

