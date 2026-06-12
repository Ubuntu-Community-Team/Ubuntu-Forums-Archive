---
title: "Wine Help"
date: 2008-10-21
forum: New to Ubuntu
---

### Post by xdarkgokux on 2008-10-21
Hi, i have installed this program called Full Tilt poker. After installation, it asks me to run it, and everything works fine. The problem is that i can't find the program once i close it i can't find it again. Its not in the .wine folder and not even in the drive c folder. It does not show up in the Applications shortcut for wine programs in the menu. However, when i run the installation again, it says that its installed and asks me to uninstall it. So where is it?? lol
Thanks..

---

### Post by Thelasko on 2008-10-21
It's in the ".wine/drive_c" folder.  Look harder.

Within the drive_c folder it's likely in the "Program Files" folder, just like it would be if it was installed in Windows.

P.S. I looked it up and the exact location should be ~/.wine/drive_c/Program Files/Full Tilt Poker/FullTiltPoker.exe

---

### Post by xdarkgokux on 2008-10-21
i know what your talking about.. i checked that already. i even copied and pasted it.. all i see is Common Files and Internet Explorer

---

### Post by Thelasko on 2008-10-21
How did you run the installation?

---

### Post by xdarkgokux on 2008-10-21
i just doubled clicked the exe file that i downloaded

---

### Post by Thelasko on 2008-10-21
And you were logged in with the same username?

---

### Post by xdarkgokux on 2008-10-21
ugh yea, i only have on user name on my computer.

---

### Post by ooobuntooo on 2008-10-21
*deleted*

---

### Post by xdarkgokux on 2008-10-21
what deleted??? did i delete it? how do i get it back?

---

### Post by xdarkgokux on 2008-10-21
what deleted??? did i delete it? how do i get it back?

---

### Post by Thelasko on 2008-10-21
Your posts are still here as far as I can tell.  I'm running out of ideas as far as what went wrong on your install.  The only thing I can think of is to check to see if the program is there in wine's version of explorer
```
wine explorer
```

---

### Post by xdarkgokux on 2008-10-22
it does not work.. and frankly i dont think its the install, this happened to google earth as well as other wine programs..but i uninstalled them..

---

