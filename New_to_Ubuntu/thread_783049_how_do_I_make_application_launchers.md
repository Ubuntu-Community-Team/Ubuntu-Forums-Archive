---
title: "how do I make application launchers?"
date: 2008-05-05
forum: New to Ubuntu
---

### Post by zeththedarkmage on 2008-05-05
I have a program that I want to make a application launcher on the toolbar for but I haven't been able to figure it out. Also the program requires me to put in sudo before running it so how can I add the sudo command to the launcher?

---

### Post by hovzio on 2008-05-05
hi, right click desktop and click add launcher. type sudo before the program  you wish to start. Right click some other launchers and look under properties for examples. You can also drag and drop programs out of the application list to create launchers.

Sorry, I didnt see that you wanted it in the toolbar, Golem XIV's post is what you want.

---

### Post by Golem XIV on 2008-05-05
Right-click on an (empty) place on the toolbar, select Add to panel, select Custom Application Launcher.  Enter the command to invoke your program in the Command field.  If it's a GUI program, replace **sudo** with **gksu** (Kubuntu uses **kdesu**).

---

### Post by jboy012000 on 2008-05-05
Hi,

I have been looking around for an answer for you I have found these links which may help.

[https://help.ubuntu.com/7.04/user-guide/C/launchers.html](https://help.ubuntu.com/7.04/user-guide/C/launchers.html)
ubuntuclips.org/videos_1.html
ubuntuforums.org/showthread.php?t=35389
[www.youtube.com/watch?v=_bTr_ohbRxo](www.youtube.com/watch?v=_bTr_ohbRxo)

Hope this helps you out.

Cheers

---

### Post by zeththedarkmage on 2008-05-05
since the program is located in the Documents folder do I need to make sure I have the full path to the program?

---

### Post by firefeather on 2008-05-05
> **zeththedarkmage said:**
> I have a program that I want to make a application launcher on the toolbar for but I haven't been able to figure it out. Also the program requires me to put in sudo before running it so how can I add the sudo command to the launcher?

If it's a graphical program, you should put gksu before it. If it's a text program (terminal stuff), you should put sudo before it.

However, either way, if I were you, I would be careful with a program that requires sudo for its use.

If you didn't need the path before, you don't need it now. However, the Documents folder isn't usually searched for programs. You will probably need to include the path; something like:

> gksu ~/Documents/yourprogram

or

> sudo ~/Documents/yourprogram

---

### Post by zeththedarkmage on 2008-05-05
Well before I was going through terminal to the folder the file was in and typing sudo ./filename

EDIT: I put in gksu ~path/to/file and when I click it nothing happens

---

### Post by firefeather on 2008-05-05
> **zeththedarkmage said:**
> Well before I was going through terminal to the folder the file was in and typing sudo ./filename

EDIT: I put in gksu ~path/to/file and when I click it nothing happens

Do you have a slash after the tilde, like this?

> ~/path/to/file

---

### Post by zeththedarkmage on 2008-05-05
it was gksu /home/user/documents/file do I need to take out the first backslash?

---

### Post by firefeather on 2008-05-05
> **zeththedarkmage said:**
> it was gksu /home/user/documents/file do I need to take out the first backslash?

No, leave it in. The first slash indicates you're starting from the root (top) directory.

---

