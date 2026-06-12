---
title: "How to 'run' programs?"
date: 2008-11-30
forum: New to Ubuntu
---

### Post by s6pnj on 2008-11-30
So, still very new to Ubuntu and feeling my way.  I am trying to get a connection working to my Humax box, but in order to do so, I need to run a program as administrator.  Now I can get into the terminal and use sudo on some things, but I'm still learning the syntax etc.

What I'd like to know is how do I run a program from the terminal, and then how do I run it as an administrator.  If I explore the folder (in Nautilus?), I get the program icon and if I click it twice, it runs the program.  I want to be able to do this from the termianl though as I can then use sudo or gksudo (which is best?).  If it has worked, I've attached a screen shot of the program I'm trying to run as administrator.  It's windows based and so runs through Wine.

What I'm trying to achieve can be found here 
[http://ubuntuforums.org/showthread.php?t=665773](http://ubuntuforums.org/showthread.php?t=665773)
Thanks!

---

### Post by ChildOfMana on 2008-11-30
As far as I know, if you're using WINE (and assuming the program runs okay under WINE), all you need to do is right-click on the executable and select 'Open With Wine' from the list of options.

If you need to be administrator then fire up a Terminal first and type;

> gksudo nautilus

This will run Nautilus (the graphical file browser) with admin rights.

---

### Post by SPr on 2008-11-30
Open a terminal and enter "cd /home/phil/Downlaods" to change to the correct folder, "gksudo wine humaxGUI" will run wine with this file.

Generally gksudo is used for programs with a gui and sudo for programs without a gui.

---

### Post by redseventyseven on 2008-11-30
sudo and gksudo essentially do the same thing (if you're typing commands into a terminal), but one asks for your password in the terminal, and the other asks for it in a graphical window.

From the manpages:

> gksu  is a frontend to su and gksudo is a frontend to sudo.  Their primary purpose is to run graphical commands that need  root  without  the need to run an X terminal emulator and using su directly.


PS - Here's a tip: if you're ever stuck with a command, there's usually a manual page (manpage for short) associated with it. To read the manual page for a command, type ```
man <command>
``` into the terminal, e.g. ```
man gksudo
```

---

### Post by s6pnj on 2008-11-30
Thanks to both.  The gksudo nautilus seems to have worked.  The gksudo wine humaxGui did something, but no program appeared, so I don't know what it did.  Brilliant!  I now need to sort out the next issue which is why can't I 'see' my files on the Humax now, ah well, off we go again!

---

