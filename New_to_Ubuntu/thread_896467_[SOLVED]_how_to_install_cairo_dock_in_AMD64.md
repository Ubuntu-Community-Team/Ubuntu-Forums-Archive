---
title: "[SOLVED] how to install cairo dock in AMD64?"
date: 2008-08-21
forum: New to Ubuntu
---

### Post by markip on 2008-08-21
I have amd64 and i want to install the cairo-dock. The problem is that i don't want to use the terminal to type commands, i want to run run it straight(.deb package maybe?). I read this [https://help.ubuntu.com/community/CairoDock](https://help.ubuntu.com/community/CairoDock) but i can't really understand what i have to do(i tried to install with this way and i failed). Can someone help me?

---

### Post by overdrank on 2008-08-21
> **markip said:**
> I have amd64 and i want to install the cairo-dock. The problem is that i don't want to use the terminal to type commands, i want to run run it straight(.deb package maybe?). I read this [https://help.ubuntu.com/community/CairoDock](https://help.ubuntu.com/community/CairoDock) but i can't really understand what i have to do(i tried to install with this way and i failed). Can someone help me?

Hi and there is links to deb packages on the link you gave
[http://developer.berlios.de/project/showfiles.php?group_id=8724](http://developer.berlios.de/project/showfiles.php?group_id=8724)

---

### Post by markip on 2008-08-21
yes but they are all for intel not amd64, i tried to install the deb package it says error wrong archtecture. I want deb for amd64

---

### Post by overdrank on 2008-08-21
> **markip said:**
> yes but they are all for intel not amd64, i tried to install the deb package it says error wrong archtecture. I want deb for amd64

Yes, and sorry as I did not read the 64 bit. Then if you do not want to use the command line I can not help
If you choose to use the command line
```
 sudo dpkg -i --force-architecture "package name".deb
```

---

### Post by markip on 2008-08-21
> **overdrank said:**
> Yes, and sorry as I did not read the 64 bit. Then if you do not want to use the command line I can not help
If you choose to use the command line
```
 sudo dpkg -i --force-architecture "package name".deb
```

i used it and there is an error(i an going to be as much specific as i can because i am greek and i have to translate in English)here it is
''no such file on directory. error during the edit of  cairo-dock.deb''
(i hope that you understand the translation)

---

### Post by Sealbhach on 2008-08-21
> **markip said:**
> i used it and there is an error(i an going to be as much specific as i can because i am greek and i have to translate in English)here it is
''no such file on directory. error during the edit of  cairo-dock.deb''
(i hope that you understand the translation)

You need to give it the exact file name as the .deb file you downloaded.

You also need to be in the same directory as the package when you issue the command - the best thing is to copy the .deb file into your /home directory.

e.g. 
```

 sudo dpkg -i --force-architecture cairo-dock_v1.6.1.2_i686.deb
```

That should do it.


.

---

### Post by markip on 2008-08-23
ok i finally managed to install it using this guide [http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=4142322](http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=4142322) anyway, thank's for the help!!!!!

---

