---
title: "help editing bashrc"
date: 2012-09-20
forum: New to Ubuntu
---

### Post by johnknott on 2012-09-20
Please advise as new to ubuntu12. I have installed Gnu radio and need to add an 
export PYTHONPATH=/x/y/z   to bashrc, I can find file and read but cannot edit as not  owner. 
How to get root privelage from GUI please.

John 2E0KNJ

---

### Post by MG&amp;TL on 2012-09-20
> **johnknott said:**
> Please advise as new to ubuntu12. I have installed Gnu radio and need to add an 
export PYTHONPATH=/x/y/z   to bashrc, I can find file and read but cannot edit as not  owner. 
How to get root privelage from GUI please.

John 2E0KNJ

Lol, which .bashrc have you found? It should be the one in your own home folder. Press Ctrl-H to see hidden files.

---

### Post by jerrrys on 2012-09-20
"How to get root privelage from GUI please."

[Open a terminal]("https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal") and enter:

gksudo nautilus

And welcome to the forums :)

---

### Post by Hadaka on 2012-09-20
Hi, you have 2 .bashrc files, one in your home directory and one in root.

to see  the file in home directory...
```
ls -a .bashrc[CODE]
to edit in your home directory....
[CODE]gedit .bashrc 
```

to get into your root directory..
```
sudo -i
```
to list .bashrc..
```
ls -a .bashrc
```
to edit in root directory....
```
gksudo gedit .bashrc
```

if this satisfies your question..please mark this as SOLVED

---

### Post by johnknott on 2012-09-21
> **Hadaka said:**
> Hi, you have 2 .bashrc files, one in your home directory and one in root.

to see  the file in home directory...
```
ls -a .bashrc[CODE]
to edit in your home directory....
[CODE]gedit .bashrc 
```

to get into your root directory..
```
sudo -i
```
to list .bashrc..
```
ls -a .bashrc
```
to edit in root directory....
```
gksudo gedit .bashrc
```

if this satisfies your question..please mark this as SOLVED

Thank you SOLVED had to use nano as gedit wanted display setting

---

### Post by BlinkinCat on 2012-09-21
> **johnknott said:**
> Thank you SOLVED had to use nano as gedit wanted display setting

John if you come back to this thread, you mark "Solved" using the thread tools at the top of page - ;)

---

