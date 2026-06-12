---
title: "How to right-click as root?"
date: 2012-02-11
forum: New to Ubuntu
---

### Post by bonedriven on 2012-02-11
For example, I want to delete a folder. I right-click on it, but the "delete" option is grayed out. How am I supposed to do that?

Thanks.

---

### Post by Learning Linux 2011 on 2012-02-11
> **bonedriven said:**
> For example, I want to delete a folder. I right-click on it, but the "delete" option is grayed out. How am I supposed to do that?

Thanks.

It depends

Sometimes you can open a terminal and type:
```

gksudo nautilus

```That will open a window that will allow you to act as root graphically.

Of course, you still can't delete the root folder though, even as root.

---

### Post by bonedriven on 2012-02-11
> **Learning Linux 2011 said:**
> It depends

Sometimes you can open a terminal and type:
```

gksudo nautilus

```That will open a window that will allow you to act as root graphically.

Of course, you still can't delete the root folder though, even as root.

Thank you! How long does the root effect last? Till I restart?

---

### Post by westie457 on 2012-02-11
Using Nautilus as root can be extremely dangerous to your system, **you can remove anything as root including the /root folder**.

Not sure exactly how ling the effect lasts because all the time that window is open you are root and when you close the window the process is still running in the terminal. Closing the terminal will give a warning about a running process. At a guess the 'root'effect lasts at least until you kill the running process and to be on the safe side after using a root Nautilus you should at least log out of the system and log in again or restart the whole system.

---

### Post by Learning Linux 2011 on 2012-02-11
Actually it only applies to that window that is open.    
When you close that window, the root goes away, unless or until you re-issue the gksudo command to open it again.
When you close the window, the terminal window is still open, so you should probably go back to the terminal window and press "Ctrl+c"
just to make sure it closes properly.

The gksudo command can be used to open almost any graphical program as root.  The "gk" stands for "graphical".
For example, you can also use gksudo to open the text editor (gedit) so you can edit files that require root access.

Like the person above me said though, you can get into alot of trouble doing things as root.  Be careful.

---

### Post by bonedriven on 2012-02-11
Thank you!

---

### Post by anewguy on 2012-02-11
+1 on being careful.  In this particular instance I would much prefer just myself to see command line usage to actually delete the file using sudo rm.  For me, I'm much more likely to accidently click on the incorrect item and delete it than I am to mistype it - in the example given it's a lot more difficult to delete root. (not sure you can if a sudo'er is active anyway).

Also, just to reiterate a standing forum policy - do *NOT* attempt in this forum to teach someone how to enable the root account.  Such threads will be modified so that the rules-offending portions are edited out, the thread will be closed, and more than likely you will here via PM something from an administrator.

---

