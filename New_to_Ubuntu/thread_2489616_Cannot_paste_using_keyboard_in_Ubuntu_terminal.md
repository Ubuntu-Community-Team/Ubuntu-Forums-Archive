---
title: "Cannot paste using keyboard in Ubuntu terminal"
date: 2023-08-04
forum: New to Ubuntu
---

### Post by crowcrowcrow on 2023-08-04
I cannot paste using my keyboard in Ubuntu terminal. Copy works (ctrl+c). I have tried ctrl+v, shift ctrl+v and shift insert.

---

### Post by Autodave on 2023-08-05
Copy your text. left click in terminal, right click for drop menu, choose "paste".  That's the only way that O have ever got it to work.

---

### Post by #&amp;thj^% on 2023-08-05
> **crowcrowcrow said:**
> I cannot paste in Ubuntu terminal. Copy works (ctrl+c). I have tried ctrl+v, shift ctrl+v and shift insert.
Can you show us this please:
```
ps -p$PPID
```

---

### Post by crowcrowcrow on 2023-08-05
ps -p$PPID
PID TTY          TIME CMD
375 ?        00:00:00 Relay(376)

---

### Post by tea for one on 2023-08-05
Using Ubuntu 22.04 with Gnome 42.9, here is the result:-
```
edited@edited-22-04:~$ ps -p$PPID
    PID TTY          TIME CMD
   3241 ?        00:00:00 gnome-terminal-
edited@edited-22-04:~$
```

Copy is Shift + Ctrl + C
Paste is Shift + Ctrl + V

---

### Post by crowcrowcrow on 2023-08-05
[**[COLOR=#000000]@tea for one[/COLOR]**]("https://ubuntuforums.org/member.php?u=585392") Please see my original post.

---

### Post by ajgreeny on 2023-08-05
Ctrl+c in terminal does not normally copy the text but cancels whatever process is running, so I'm surprised that you can get copy to work that way.

As mentioned by tea for one above 
[B][I]Copy is Shift + Ctrl + C
Paste is Shift + Ctrl + V [/I][/B]
are the default keyboard shortcuts for copy/paste so something seems strange about what you're seeing with your keyboard shortcuts..

---

### Post by tea for one on 2023-08-05
> **crowcrowcrow said:**
> [**[COLOR=#000000]@tea for one[/COLOR]**]("https://ubuntuforums.org/member.php?u=585392") Please see my original post.
Yes, I have seen your original post.
However, in post no. 4, you do not report gnome-terminal.
Your result below:-
```
ps -p$PPID
PID TTY TIME CMD
375 ? 00:00:00 Relay(376) 
```

---

### Post by #&amp;thj^% on 2023-08-05
> **tea for one said:**
> Yes, I have seen your original post.
However, in post no. 4, you do not report gnome-terminal.
Your result below:-
```
ps -p$PPID
PID TTY TIME CMD
375 ? 00:00:00 Relay(376) 
```

+1
or in my case
```
ps -p$PPID
    PID TTY          TIME CMD
   7710 ?        00:03:47 xfce4-terminal

```
Are you sure it's gnome-terminal?
```
apt policy gnome-terminal
gnome-terminal:
  Installed: (none)
  Candidate: 3.48.0-1ubuntu1
  Version table:
     3.48.0-1ubuntu1 500
        500 http://us.archive.ubuntu.com/ubuntu lunar/main amd64 Packages

```

---

### Post by grahammechanical on 2023-08-05
In Ubuntu 20.04 (and I guess upwards) open the terminal and click on the hamberger icon (3 horizontal lines). Select Preferences. Select Shortcuts. There we see

Copy = Shift+Ctrl+C   Paste = Shift+Ctrl+V

All the shortcuts are in the Preferences dialog.

Regards

---

### Post by crowcrowcrow on 2023-08-05
Sorry, I should have provided more information in my post. I am running Ubuntu as a virtual machine in Windows. That output from ps -p$PPID is from running Ubuntu in Powershell. The reason I am not running Tilix is that the font is too small for me to read comfortably and I am unable to change it. I cannot input or change any of the fields in Profile.

---

### Post by MAFoElffen on 2023-08-06
So rather that a Graphical Terminal inside of Ubuntu, you are running Ubuntu in WSL.

You probably should have mentioned that in your original post.

WSL runs in a Windows Command prompt window. To do copy /paste in that:
 - Open a command line window.
 - Right-click an empty part of the title bar and select "Properties"
 - Select the "Use Ctrl + Shift + C / V as Copy/Paste" option, and then click the "OK" button.

---

### Post by crowcrowcrow on 2023-08-06
Got it, thank you.

---

