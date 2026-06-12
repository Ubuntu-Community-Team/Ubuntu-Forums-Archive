---
title: "permissions problem"
date: 2008-07-03
forum: New to Ubuntu
---

### Post by eason1 on 2008-07-03
hello, I'm kinda new to linux and am having trouble moving certain files because of permissions issues. I am the only user on the system and have root access in terminal through sudo cmd, but when using gui cannot move sound files into usr/share/sounds folder to play my own wav. files for login and out sounds. If someone could help me either figure out how to gain root in the GUI or at least how to move the files in terminal I would greatly appreciate it.

---

### Post by drs305 on 2008-07-03
> **eason1 said:**
> hello, I'm kinda new to linux and am having trouble moving certain files because of permissions issues. I am the only user on the system and have root access in terminal through sudo cmd, but when using gui cannot move sound files into usr/share/sounds folder to play my own wav. files for login and out sounds. If someone could help me either figure out how to gain root in the GUI or at least how to move the files in terminal I would greatly appreciate it.

Probably what you want is to open nautilus with administrator privileges:
```
gksudo nautilus
```

You use "gksudo" with graphical apps and "sudo with terminal commands that will not invoke a gui-based app.

You can also move files there with the "sudo mv" commands or copy files there with "sudo cp" command.

---

### Post by spiderbatdad on 2008-07-03
To move/edit files via GUI run in a terminal:```
gksu nautilus
```

hmmm. too slow!

---

### Post by eason1 on 2008-07-03
Thanks guys, I was able to move what i needed. For some reason though, I cant get it to play the sounds I put in, or even play the defaults anymore. Weird

---

### Post by drs305 on 2008-07-03
> **eason1 said:**
> Thanks guys, I was able to move what i needed. For some reason though, I cant get it to play the sounds I put in, or even play the defaults anymore. Weird


On my hardy system, all the folders in /usr/share/sounds are owned by root and have 755 permissions. All the files within the folders have 644 permissions

---

### Post by superprash2003 on 2008-07-03
right click on the file you want to play and click on properties and go to permissions... and post what permissions are set currently

---

### Post by ZabiGG on 2008-07-03
Hi and welcome to Ubuntu :)

For great pointers about using the terminal and taming it (it's really convenient and fast once you start using it), check out this link:

[http://ubuntuforums.org/showthread.php?t=73885](http://ubuntuforums.org/showthread.php?t=73885)

It also includes a great section on permissions that might help you understand their use better.

For additional starter info, just click on the Look here link in my signature.

Hope this helps and happy exploring :)

Z.

---

