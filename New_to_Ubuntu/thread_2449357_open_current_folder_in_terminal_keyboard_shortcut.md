---
title: "open current folder in terminal keyboard shortcut"
date: 2020-08-25
forum: New to Ubuntu
---

### Post by bartalor on 2020-08-25
Hi I have Ubuntu 20.04 and I want to have a keyboard shortcut to open the terminal in the current folder I am in (I know that ctrl+alt+T opens the terminal, but it opens it in the home directory).
so from googling my problem a bit I saw that installing nautilus-open-terminal package might help, but it seems that the package does not exist,
and from checking existing packages I saw that the closest thing to it is caja-open-terminal but it doesn't seem to help.
If some of you have any idea about these things, it would help a lot.

Edit: Solved.

thanks :)

---

### Post by tea for one on 2020-08-25
Assuming that you have navigated to your destination folder via Nautilus (Files) 

Right click > Open in Terminal

Not strictly a keyboard shortcut but still useful.

---

### Post by bartalor on 2020-08-25
yeah I know that, but doing it from the keyboard is important to me.

---

### Post by deadflowr on 2020-08-25
Try installing nautilus-extension-gnome-terminal

Edit: Note you need to quit and restart nautilus in order for anything to take affect.
(Logging out and back in works too)


Double Edit: I'm fairly sure this package will give an option to open the current directory selected in Files( nautilus) in a terminal,
I am not sure it can do anything about setting a specific keyboard shortcut.

---

### Post by bartalor on 2020-08-26
> **tea for one said:**
> Assuming that you have navigated to your destination folder via Nautilus (Files) 

Right click > Open in Terminal

Not strictly a keyboard shortcut but still useful.

> **deadflowr said:**
> Try installing nautilus-extension-gnome-terminal

Edit: Note you need to quit and restart nautilus in order for anything to take affect.
(Logging out and back in works too)


Double Edit: I'm fairly sure this package will give an option to open the current directory selected in Files( nautilus) in a terminal,
I am not sure it can do anything about setting a specific keyboard shortcut.

Finally found a solution that worked for me, if your'e also interested, here it is:
[https://askubuntu.com/questions/1194329/create-new-file-keyboard-shortcut-ubuntu-18-04](https://askubuntu.com/questions/1194329/create-new-file-keyboard-shortcut-ubuntu-18-04)

---

### Post by vanadium on 2020-08-27
See a method [here]("https://askubuntu.com/a/1079882/558158") that does not require installing additional software.

---

