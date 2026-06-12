---
title: "hot can I ad a launcher or to a menu?"
date: 2006-08-04
forum: Packaging and Compiling Programs
---

### Post by Kilz on 2006-08-04
I have compiled a .deb of a program, but how can I add a launcher to the desktop, or add it to the Application menu?

---

### Post by Jose Catre-Vandis on 2006-08-04
right Click on Desktop
Select Create Launcher
Enter details including command line entry you use to start the program
choose icon if you wish
Drag icon to menu bar (you can then delete the one on the desktop OK)

To add to applications menu
Applications>Accessories>Alacarte Menu Editor
Choose section
File>New
Do as for normal launcher
Job done

---

### Post by VirtuAlex on 2006-08-04
I think Kilz is asking how installer can create launcher...

---

### Post by Jose Catre-Vandis on 2006-08-04
> **VirtuAlex said:**
> I think Kilz is asking how installer can create launcher...

On a second read, me thinks you're right :rolleyes:

---

### Post by ssam on 2006-08-05
you need to put a .desktop file in /usr/share/applications

there are plenty of examples there to look at.

---

### Post by Kilz on 2006-08-05
Thanks for the quick answers, and yes I was asking how the installer can add it. I should have been a little more clear on that.

---

### Post by VirtuAlex on 2006-08-05
My best guess is to add appropriate install command into Makefile and rebuild deb with whatever methods you're using.

---

### Post by Kilz on 2006-08-05
> **ssam said:**
> you need to put a .desktop file in /usr/share/applications

there are plenty of examples there to look at.

I tried this method, and couldnt get the app to show in the menu. I can see the .desktop file, its basicly a launcher in /usr/share/applications. But it doesnt show in the menu.

[quote=VirtuAlex]My best guess is to add appropriate install command into Makefile and rebuild deb with whatever methods you're using.[/quote]
Yes, but the question is what kind of file and where is it installed.

---

### Post by VirtuAlex on 2006-08-05
> **Kilz said:**
> Yes, but the question is what kind of file and where is it installed.
It seems that if you put the file in ~/.local/share/applications and edit xml in ~/.config/menus/applications.menu then link appears in the menu... but there should be other way. Post if you find out.

---

### Post by dusu on 2006-08-05
> **Kilz said:**
> I tried this method, and couldnt get the app to show in the menu. I can see the .desktop file, its basicly a launcher in /usr/share/applications. But it doesnt show in the menu.


Yes, but the question is what kind of file and where is it installed.

Hi,
not sure if this is what you want, but to add an application in the menus, one way is to add a file in /usr/share/menu
(the file should have the name of your application, have a look in there to see what the file should look like).
Then you can do
```
sudo update-menus
```
but for this, I think you need to have installed the package called menu.

---

### Post by Kilz on 2006-08-05
Thanks to everyone who replied, I figured out what I was doing wrong. I was making a launcher named comical.desktop because I thought .desktop files were launchers. But I opened up one of the /usr/share/application .desktop files with the test editor and found they have a lot more information than a normal launcher.

---

### Post by H.E. Pennypacker on 2006-08-15
> **Kilz said:**
> Thanks to everyone who replied, I figured out what I was doing wrong. I was making a launcher named comical.desktop because I thought .desktop files were launchers. But I opened up one of the /usr/share/application .desktop files with the test editor and found they have a lot more information than a normal launcher.

So, in the end, what did you do?  Can you provide a guide?

---

### Post by Kilz on 2006-08-15
> **H.E. Pennypacker said:**
> So, in the end, what did you do?  Can you provide a guide?

I basicly opened up a launcher in /usr/share/applications with gedit, copied the info, pasted it to a new file, and edited it to the application I wanted to launch. Then added it to the deb file.

---

