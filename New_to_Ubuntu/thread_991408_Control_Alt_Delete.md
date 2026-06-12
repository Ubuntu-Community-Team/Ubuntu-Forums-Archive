---
title: "Control Alt Delete"
date: 2008-11-23
forum: New to Ubuntu
---

### Post by icyest on 2008-11-23
Wheres the control alt delete function for ubuntu? I feel like I'm blind when I don't know whats going on. I hear audio, but no windows are open. control tab just doesn't cut it.

---

### Post by DGortze380 on 2008-11-23
ctrl+alt+backspace  -- restart X. Logs you out, restarts X Window System, helpful for frozen programs.

Add System Applet to task bar -- similar to ctrl-alt-del window in windows

conky  --  displays a variety of system monitoring info on your desktop.

---

### Post by jakupl on 2008-11-23
I usually go to terminal and enter

```
ps -A
```

That shows all processes. To kill a process, enter

pkill *name-of-proces*

you can also use top. Try to enter "top" in terminal

---

### Post by jimreynold2nd on 2008-11-23
DGortze was right. I just wanna add:
1. Rightclick the panel, choose "Add to panel", find the "Force Quit" applet. You can even assign hotkey to it. This is easier than resarting X.
2. The l33t way: Ctlr-Alt-F1, login to the tty, do
```
ps -A | grep 'name of the program'
```
look for it's pid. Then do 'kill' the pid.
For example:
```

$ ps -A | grep firefox
8598 ? 00:00:18 firefox
$ kill 8598

```

---

### Post by jimreynold2nd on 2008-11-23
DGortze was right. I just wanna add:
1. Rightclick the panel, choose "Add to panel", find the "Force Quit" applet. You can even assign hotkey to it. This is easier than resarting X.
2. The l33t way: Ctlr-Alt-F1, login to the tty, do
```
ps -A | grep 'name of the program'
```
look for it's pid. Then do 'kill' the pid.
For example:
```

$ ps -A | grep firefox
8598 ? 00:00:18 firefox
$ kill 8598

```

---

### Post by jimreynold2nd on 2008-11-23
sorry about doublepost.

---

### Post by ibuclaw on 2008-11-23
You can set this hotkey up in gnome. Although, Control, Alt and Delete is already taken by the logout feature.

Press **Alt+F2** and type in **gconf-editor**

Next, scroll down the folder listings and enter **apps -> metacity**

Click the **global_keybindings** folder and scroll down the key listing till you see **run_command_1**

Double-click the Value and type in the key combination you want:

It's a simple, easy configuration to type out. Some examples of unused hotkeys:

<Control><Alt>T

<Control><Alt>P

<Control><Alt>Return

Something that you'll find easy to press ;)


Once you've decided on a key combination, click the **keybinding_commands** folder and find the **command_1** key, double-click it and enter in the command you want to run when you press that key combination.

ie: For the gnome-system-monitor, type in:

gnome-system-monitor


Now quit the gconf-editor and tryout your new hotkey command ;)

Regards
Iain

---

### Post by semitone36 on 2008-11-23
Ctrl + Alt + Del is a windows command.  Its best if you forget everything you thought you knew from windows about computers if you are trying to learn linux.  For a process monitor in Ubuntu go to System -> Administration -> System Monitor and select the Processes Tab.

Another useful tool is to type "top" into the terminal.

---

### Post by icyest on 2008-11-25
I really don't understand the second part of your response. There is no area to type in "gnome-system-monitor". When I double click Command 1 key, there is a box that just says "Value:" 

No other text box is available. 
Since I know that control+alt+delete is already taken up by the logout/logoff menu, how do I change that from the default, to what I want? It seems like I have to replace that value somewhere. 

I don't mean to be rude, but cant you just write out your instructions as you are doing the process yourself? It makes life a lot easier.

> **tinivole said:**
> You can set this hotkey up in gnome. Although, Control, Alt and Delete is already taken by the logout feature.

Press **Alt+F2** and type in **gconf-editor**

Next, scroll down the folder listings and enter **apps -> metacity**

Click the **global_keybindings** folder and scroll down the key listing till you see **run_command_1**

Double-click the Value and type in the key combination you want:

It's a simple, easy configuration to type out. Some examples of unused hotkeys:

<Control><Alt>T

<Control><Alt>P

<Control><Alt>Return

Something that you'll find easy to press ;)


Once you've decided on a key combination, click the **keybinding_commands** folder and find the **command_1** key, double-click it and enter in the command you want to run when you press that key combination.

ie: For the gnome-system-monitor, type in:

gnome-system-monitor


Now quit the gconf-editor and tryout your new hotkey command ;)

Regards
Iain

---

### Post by Paqman on 2008-11-25
> **jakupl said:**
> I usually go to terminal and enter

```
ps -A
```

That shows all processes. To kill a process, enter

pkill *name-of-proces*

you can also use top. Try to enter "top" in terminal

There's also a simple way of doing this for graphical apps:

Alt-F2 > type xkill > click on the misbehaving app.

---

### Post by bluemm on 2008-11-25
good thread with good tips, thanks to everyone who contributed.

---

### Post by icyest on 2008-11-28
My system monitor simply indicates that I have gnome-system-monitor running. I clearly have firefox running. Is this really the equivalent of task manager found in microsoft?

---

### Post by theozzlives on 2008-11-28
> **semitone36 said:**
> Ctrl + Alt + Del is a windows command.  Its best if you forget everything you thought you knew from windows about computers if you are trying to learn linux.  For a process monitor in Ubuntu go to System -> Administration -> System Monitor and select the Processes Tab.

Another useful tool is to type "top" into the terminal.


  I learned the hard way, now working on Linux+

---

### Post by icyest on 2008-11-29
What are you talking about? Who's suppose to know what Linux+ is? It's not even searchable in google.

---

### Post by ratmandall on 2008-11-29
You can add a CTRL+ALT+DELETE shortcut to gnome-system-monitor through >System>Preferences>Keyboard Shortcuts

---

