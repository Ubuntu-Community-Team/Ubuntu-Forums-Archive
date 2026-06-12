---
title: "Commands"
date: 2008-10-19
forum: New to Ubuntu
---

### Post by Obuleshu Gumpu on 2008-10-19
How to execute one command in all folders in current directory?

I have to execute the following command in each folder where each folder contains a make file and I would like to create one patch of all folders.
make DESTDIR=/tmp/patch install

Obuleshu Gumpu

---

### Post by Idefix82 on 2008-10-19
What exactly do you want to do?

---

### Post by Obuleshu Gumpu on 2008-10-19
I have to execute the following command in each folder where each folder contains a make file and I would like to create one patch of all folders.
 make DESTDIR=/tmp/patch install
-Obuleshu Gumpu

---

### Post by Idefix82 on 2008-10-19
Try
```
find /your/starting/folder -type d -execdir your command \;
```
In your command, if you actually need to use the name of the folder somewhere you do it with '{}'. For example
```
find /your/starting/folder -type d -execdir cp '{}' /backup \;
```
copies each folder into the backup folder.

---

### Post by Obuleshu Gumpu on 2008-10-20
Thanks for your help 
I tried the command given but I got  error 

find: invalid predicate `-execdir'

Thanks 
-Obuleshu Gumpu

---

### Post by stephanvaningen on 2008-10-20
This worked for me:
```
find /home/stephan/Desktop -type d -execdir ls \;
```
Can you please copy/paste your command, excactly as you typed it in the terminal?

---

