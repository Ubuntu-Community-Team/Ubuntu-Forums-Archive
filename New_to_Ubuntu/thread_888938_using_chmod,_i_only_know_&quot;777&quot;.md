---
title: "using chmod, i only know &quot;777&quot;"
date: 2008-08-13
forum: New to Ubuntu
---

### Post by WinterMadness on 2008-08-13
for example if I was triyng to move a folder I dont have permission with i would sudo chmod 777 foldr1

how do I change it back? or to something more secure? 
even giving me basic numers to use woudl help, describing what it does

---

### Post by Thingymebob on 2008-08-13
```
owner group others
 rwx   rwx   rwx

```
r=4 w=2 x=1

add them up for each section so 
owner read-write-execute (rwx)=7
group read-execute(r-x)=5
others read-execute(r-x)=5

chmod 755

---

### Post by ConMan318 on 2008-08-13
Read = 4
Write = 2
Execute = 1

You choose numbers by adding those together, for example 7 = 4 + 2 + 1, so 7 means that the group has the ability to read, write, and execute a file.  If you don't want people to be able to change a file, but want to allow them to read/execute it, 4 + 1 = 5, so put a 5.

The order of the numbers is User, Group, Others.

```

user   group  others
7      5      4

```
so "chmod 750" will give you, the user, complete access.  It will give other members of the group the ability to read/execute, but not write.  And users not in your group can only read the file.

Just do the math for each specific file and decide who should be able to do what.



EDIT: Got beaten to it :p.

---

### Post by scorp123 on 2008-08-13
> **WinterMadness said:**
>  for example if I was triyng to move a folder I dont have permission And there is maybe a good reason you don't have the permission to do it! Maybe it's a system folder you shouldn't mess around with? But can you please go into more details and explain what folder you tried to manipulate?

> **WinterMadness said:**
>  even giving me basic numers to use woudl help, describing what it does  There is a wonderful manual waiting for you to explore ... Best of all: it comes with every Ubuntu installation. So please open a terminal and enjoy reading: ```
man chmod
``` ... You should find the upper 30 or so lines quite interesting. ;)

---

### Post by WinterMadness on 2008-08-13
> **scorp123 said:**
> And there is maybe a good reason you don't have the permission to do it! Maybe it's a system folder you shouldn't mess around with? But can you please go into more details and explain what folder you tried to manipulate?

 There is a wonderful manual waiting for you to explore ... Best of all: it comes with every Ubuntu installation. So please open a terminal and enjoy reading: ```
man chmod
``` ... You should find the upper 30 or so lines quite interesting. ;)



nah it was an icon folder

thanks everyone!

---

### Post by oldos2er on 2008-08-13
> **WinterMadness said:**
> for example if I was triyng to move a folder I dont have permission with i would sudo chmod 777 foldr1

how do I change it back? or to something more secure? 
even giving me basic numers to use woudl help, describing what it does

 No need to change permissions. In a terminal, use "sudo mv /something /somewhere", or type "gksudo nautilus" in a terminal to give you graphical admin access.

---

