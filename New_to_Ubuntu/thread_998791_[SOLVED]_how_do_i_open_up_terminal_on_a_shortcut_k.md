---
title: "[SOLVED] how do i open up terminal on a shortcut key?"
date: 2008-12-01
forum: New to Ubuntu
---

### Post by shiningkenmonster on 2008-12-01
this is going to sound dumb. but how do i open up terminal on the shortcut key?

also, is there a list of all shortcut keys on the ubuntu somewhere?

---

### Post by stephanvaningen on 2008-12-01
```
gnome-terminal
```

---

### Post by shiningkenmonster on 2008-12-01
yeah thanks. I already know you can press the F2 + ALT and type in 'gnome-terminal' to run the open the terminal. i was wondering if there was a faster way to open terminal with a shortcut key.

and also a list of shortcut keys

---

### Post by Paddy Landau on 2008-12-01
> **shiningkenmonster said:**
> how do i open up terminal on the shortcut key?

[LIST=1]
[*]Go to System -> Preferences -> Advanced Desktop Effects Settings. If you don't have that in your Preferences menu, then:
[LIST=1]
[*]Go to System -> Administration -> Synaptic Package Manager
[*]Install compiz.
[/LIST]
 
[*]Go to General Options.
[*]Select the "Commands" tab.
[*]Run "Run terminal command":
[LIST=1]
[*]The Terminal command line should read gnome-terminal
[*]Next to "Open a terminal", press the button and choose the keyboard shortcut. Take care not to choose one that conflicts with something else.
[/LIST]
 
[/LIST]
Hope that helps.

---

### Post by Kosimo on 2008-12-01
> **shiningkenmonster said:**
> yeah thanks. I already know you can press the F2 + ALT and type in 'gnome-terminal' to run the open the terminal. i was wondering if there was a faster way to open terminal with a shortcut key.

and also a list of shortcut keys

Use gnome-do

It is extremely fast and it works not only for terminal for almost all apps

---

### Post by Paddy Landau on 2008-12-01
> **shiningkenmonster said:**
> is there a list of all shortcut keys on the ubuntu somewhere?
I don't know if there's a comprehensive list of shortcuts.

Here is one:
System -> Preferences -> Keyboard Shortcuts

---

### Post by sujoy on 2008-12-01
> **shiningkenmonster said:**
> this is going to sound dumb. but how do i open up terminal on the shortcut key?

also, is there a list of all shortcut keys on the ubuntu somewhere?

just for the kicks, try out guake or tilda. (quake like dropdown consoles)

---

### Post by scorp123 on 2008-12-01
> **shiningkenmonster said:**
> how do i open up terminal on the shortcut key? **System > Preferences > Keyboard Shortcuts** ... then scroll down to the **"Run a terminal"** action ... click on it and voila, you can define your shortcut. I personally set mine to **Ctrl+Alt+T **... it seems no other application uses that combo, so far it works fine.

So whenever I press Ctrl+Alt+T anywhere ... taddaaa! A terminal opens right in front of me. :)

---

