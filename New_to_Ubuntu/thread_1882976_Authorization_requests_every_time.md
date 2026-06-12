---
title: "Authorization requests every time"
date: 2011-11-18
forum: New to Ubuntu
---

### Post by Juls. on 2011-11-18
Hi all,
I'm new in ubuntu (installed it before 1 week). I've installed Ubuntu 11.10 and then installed Kubuntu Desktop Plasma. When I log with my user and that KDE, and try to apply system updates for example.....the updater tells me that I need an authorization, that happen with all the programs that I start (need authorization, and can't apply anything that i make). My solution to this is to start every program manually from the terminal using the "sudo" command. So my question is: Is there any way when I start any program, when it needs root access, just to ask me for password (like GNOME), or is there a button or a keys shortcut to press an opens a dialog that asks me for root password. Because I do not see any meaning to shortcut icons when I always have to start the applications from the terminal

Thanks in advance,
Julian

---

### Post by SeijiSensei on 2011-11-18
I've only installed Kubuntu directly and never see this problem.

However you can try editing the menu items and telling the appropriate ones to run as root.  Right-click the K start button, pick Menu Editor, select an application, and choose Advanced.  You can then enter root in the "run as a different user" field.

---

### Post by Juls. on 2011-11-20
I've try this, but not worked for me. Does it mean that If I want to use KDE with ubuntu, I have to install kubuntu instead ubuntu with Kubuntu Plasma Desktop?

---

### Post by Elfy on 2011-11-20
Try running something that should not need authorisation from a terminal and post what you see in the terminal

```
kate
```

---

### Post by Juls. on 2011-11-21
juls@juls:~$ kate
X Error: BadWindow (invalid Window parameter) 3
  Major opcode: 20 (X_GetProperty)
  Resource id:  0x62000c4


This is what I get when I try to save a file. When I just open "kate", an empty line appears. When I try to save the file, the following 3 lines appear.

Regards,
Julian

---

