---
title: "Install an Application in Ubuntu 20.04 into VirtualBox."
date: 2021-01-29
forum: New to Ubuntu
---

### Post by elioi on 2021-01-29
The application is a .deb file extension. Works on Ubuntu 16.04.
I tried to run it in Ubuntu 20.04 but only the application icon came out. When I double click on the icon it starts spinning but nothing happens. How can I debug to check all processes where it stops? Could be possible some issues related Python code 2/3?  Also I need that dpkg works but I run the command sudo top and it doesn't come up. Do you have any suggestions?

---

### Post by TheFu on 2021-01-29
It is highly unlikely that a binary package from 16.04 will run on a 20.04 system. All the underlying libraries have changed. Look for an updated version or better, see if the program isn't part of the Canonical repos for 20.04 or a PPA for 20.04.  Installing a .deb file is almost the last way in the preferred list of ways that people should be using these days.

---

### Post by ajgreeny on 2021-01-29
> **TheFu said:**
> It is highly unlikely that a binary package from 16.04 will run on a 20.04 system. All the underlying libraries have changed. Look for an updated version or better, see if the program isn't part of the Canonical repos.

^^^^ +1 ^^^^
It might be worth in your 20.04 VM trying command ```
sudo apt install /path/to/your.deb
``` using the full pathway of the deb of course.

Package installation using dpkg does not deal with nor install any dependencies needed by the package but apt does this automatically, so if by chance those dependencies are still available in 20.04 repos you may be lucky, though I expect this will not be the case; things have changed greatly since 2016!

---

### Post by elioi on 2021-01-30
Hi TheFu, I installed the file using the code that you suggested. The problem is that I can see only the icon of the application. Could I use a command to se the processes, so I could see in which point it will stop. Such as the command ps. but with the file .deb it doesn't work

---

### Post by CelticWarrior on 2021-01-30
You can run it in terminal. It'll give an error message.

---

### Post by ActionParsnip on 2021-01-30
Terminal is so much more useful than the GUI offering and actually gives reasons for issues rather than just "nah"

---

### Post by TheFu on 2021-01-30
> **ActionParsnip said:**
> Terminal is so much more useful than the GUI offering and actually gives reasons for issues rather than just "nah"

Or nothing at all - just not working.
Run the program in a terminal - there are like 20 different terminal programs - it doesn't matter which one you use. When you run it, there will probably be messages output. Those messages will probably say what the problem is.  READ THEM.  Don't let your eyes gloss over.  READ THE OUTPUT.  Sometimes it will say cannot find X.  If it does, that's a problem.  Fix it or give up.

As for making some icon show up somewhere, that's GUI thing and I can't help. I barely use GUIs or menus.

---

