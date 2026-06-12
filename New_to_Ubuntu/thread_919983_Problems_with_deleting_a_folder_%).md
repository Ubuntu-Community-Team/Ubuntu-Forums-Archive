---
title: "Problems with deleting a folder %)"
date: 2008-09-14
forum: New to Ubuntu
---

### Post by zloygame on 2008-09-14
I need to delete a folder that can be deleted only with root priveleges=)

What I'm asking for is - how?
As far as I understood, such operation can be done only through terminal... %) 

Help!

---

### Post by ChanServ on 2008-09-14
you can do sudo nautilus

---

### Post by doctorbighands on 2008-09-14
Open a terminal window and type the following command:

```
sudo rm -r <file path>
```

Where "<file path>" is the location of the folder you want to delete.

You can also drag the folder into the terminal window if you're not sure of the path.

A word of caution: Be VERY careful when deleting folders. You don't want to remove something unless you're absolutely, positively certain you can do without it!

---

### Post by adult swim on 2008-09-14
instead of sudo nautilus, use gksudo nautilus.   it is recommended to use gksudo whenever you are going to use a gui

---

### Post by OutOfReach on 2008-09-14
Or to be safer, you can goto the terminal and launch nautilus with root privileges and delete the folder from there.
```
gksu nautilus
```

---

### Post by mikewhatever on 2008-09-14
Through terminal is the most common way, but there is GUI too.
Press alt+f2, type gksudo nautilus, enter your password, navigate to the folder in question and delete it.
CLI may not be easier to use, but sure is easier to give instructions in:
> sudo rm -r /path-to-folder

If you prefer the GUI way, create a launcher on the desktop by right clicking somewhere, selecting 'Create Launcher...' and entering gksudo nautilus in the command field.

---

### Post by t0p on 2008-09-14
You don't want to use terminal?  Then press **Alt+F2**, type 
```
gksudo nautilus
```

into the Run box that appears.  A File Manager window will appear - use it to navigate to the file you want to delete.

But beware! - this file manager has **root privileges** which means any boo-boos could be serious :s

---

### Post by zloygame on 2008-09-14
thank u guys a lot!
quick question, how do I uninstall kTorrent? (is it possible to do that thru the terminal? If yes - how?)

---

### Post by adult swim on 2008-09-14
sudo apt-get remove ktorrent

---

### Post by Yannick Le Saint kyncani on 2008-09-14
/me wonders which kind of directory that belonged to root the OP did delete ...

---

### Post by zloygame on 2008-09-14
i deleted qutim folder =) 
im 110% sure that it didnt affect my computer =)
its just for some unknown reason this folder got a protection, so I wasnt able to delete it without root -)

---

### Post by starcannon on 2008-09-14
> **Yannick Le Saint kyncani said:**
> /me wonders which kind of directory that belonged to root the OP did delete ...

Might have been something on his desktop, I've had ownership problems occasionally when I copy files from a usb drive.

---

### Post by starcannon on 2008-09-14
> **zloygame said:**
> i deleted qutim folder =) 
im 110% sure that it didnt affect my computer =)
its just for some unknown reason this folder got a protection, so I wasnt able to delete it without root -)

The default Pidgin is an excellent IM anyway.

---

### Post by zloygame on 2008-09-14
i know, its great, but pidgin had some problems with russian language (when people were sending me their message in russian from ICQ 6 i had problems with encoding :((

---

