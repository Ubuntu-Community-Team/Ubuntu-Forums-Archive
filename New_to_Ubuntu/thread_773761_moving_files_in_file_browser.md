---
title: "moving files in file browser"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by deembee on 2008-04-29
Hi I'm totally new to linux and are trying to move some files around for a touch screen driver in file browser but it won't let me it says i don't have permission. Is it possible to drag and drop files like I can in windows as i don't want to have to use the shell. I can't see why i can't do this I thought it would just ask for my password and let me. I find it kinda backwards to have to enter the shell to move files 

can someone let me know if it is possible 

thanks

---

### Post by lizzard on 2008-04-29
You need to be root-user to move files that are not in your home-directory around. Type "gksu nautilus"  in a terminal to run nautilus with root permissions.

---

### Post by Michael.Godawski on 2008-04-29
You can open the file browser with superuser privileges with the terminal command:

```
gksudo nautilus
```

But be sure you know what you do, because in this mode the important system files can be easily deleted and your system is nuked.

---

### Post by Gazneth on 2008-04-29
To open a GUI window with admin permissions, go to the terminal and type```
gksudo nautilus
``` gksudo is the graphical sudo comand and nautilus is the name of ubuntu's file browser. Be very careful what you use this for. With full admin rights it is possible to break your system.

---

### Post by deembee on 2008-04-29
thanks for the quick reply I'm aware of potential probs but have ubuntu installed on a junk pc to learn so if i have to reinstall i have to reinstall

---

### Post by Michael.Godawski on 2008-04-29
No worry. I had to reinstall Gutsy many times in the beginning because I've just done a no-no. But that's the way I learned a lot.

---

