---
title: "[SOLVED] cant  edit files?"
date: 2008-08-09
forum: New to Ubuntu
---

### Post by rixtr66 on 2008-08-09
im trying to edit /etc/apt/sources.list but i dont know what command to use for editing,im used to gnome gedit.when i try to use kate i get a message that says kate cant connect to x?
help!!please.:confused:
rick

---

### Post by cgkades on 2008-08-09
where are you trying to run kate from? terminal? did you issue the command sudo before it? what was the actual command you are running?

---

### Post by munkyeetr on 2008-08-09
try using
```

kdesu kwrite /etc/apt/sources.list

```

---

### Post by rixtr66 on 2008-08-09
this is what i get when i try to edit;
root@kubuntu-1:/home/rick# kdesu kwrite /etc/apt/sources.list
No protocol specified
kdesu: cannot connect to X server :0.0
root@kubuntu-1:/home/rick# kwrite /etc/apt/sources.list
No protocol specified
kwrite: cannot connect to X server :0.0
root@kubuntu-1:/home/rick#     ??  
rick

---

### Post by iaculallad on 2008-08-09
kdesu didn't work even as root? (w/c should not be the case, you just have to do **kwrite /etc/apt/sources.list** and omit kdesu. 

On your terminal, try:

```
xhost +
```

as the user- it should come back with something like "access control disabled, clients can connect from any host"

Then, just do **su** in your terminal, input your password and run **kwrite /etc/apt/sources.list**


When you're finish editing, Save and Close and issue the command below on your terminal:

```
xhost -
```

EDIT: More info - xhost: server access control program for X

```
man xhost
```

---

### Post by munkyeetr on 2008-08-09
Read this: [http://www.linuxquestions.org/questions/linux-newbie-8/kwrite-cannot-connect-to-x-server-0.0-582344/](http://www.linuxquestions.org/questions/linux-newbie-8/kwrite-cannot-connect-to-x-server-0.0-582344/)

EDIT: iaculallad beat me to the same vein of solution.

---

### Post by rixtr66 on 2008-08-09
i did every thing you said,and it opened the file,and edit but i cant save.
it says i dont have write access.
rick

---

### Post by iaculallad on 2008-08-09
> **rixtr66 said:**
> i did every thing you said,and it opened the file,and edit but i cant save.
it says i dont have write access.
rick

Did you issue the su command first? Then input the command kwrite /etc/apt/sources.list.

---

### Post by rixtr66 on 2008-08-09
no,but itried kdesu kwrite again and this time it worked!
thanksforthehelp!!!!!
rick:)

---

