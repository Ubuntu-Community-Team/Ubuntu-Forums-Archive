---
title: "Unity and other programs somehow got uninstalled"
date: 2013-08-26
forum: New to Ubuntu
---

### Post by T2manner on 2013-08-26
Hello,
I don't know how it happened, but when I turned my computer on I no longer had unity installed.  I knew it was uninstalled because when I tried to run 
```
unity
```, a message appeared saying that unity was not installed.  I also noticed Ubuntu software center was uninstalled as well as gnome-terminal.  I do not know how any of this happened because the last time I was on my computer, I installed dropbox, which used ubuntu software center.

Do you think my computer has been compromised?  This has me worried.

---

### Post by jonnyboysmithy on 2013-08-27
If someone compromised your computer most probably they would try to keep quiet about it so that you don't notice. Its highly unlikely that the cause of the problem is a compromise.
Most likely the ubuntu-desktop package got uninstalled somehow. With the package come all the things for the ubuntu desktop (unity, software centre, text editor, firefox, and all the rest).
You can install it by running:
```
sudo apt-get install ubuntu-desktop
```
in a terminal. It will tell you if its already installed.
Let us know how it goes :)

---

### Post by newb85 on 2013-08-27
I think [s]alt+F5[/s] will get you to a fullscreen CLI, since gnome-terminal is no longer installed.

Edit: It's Ctrl+Alt+F1, as Jonathan points out below.

---

### Post by verymadpip on 2013-08-27
I was under the impression that the "*buntu-desktop" packages were meta-packages pointiing to all the other "stuff", so uninstalling wouldn't break anything.
Of course I could be completely wrong about that.
I don't suppose a reinstall of the desktop would hurt too much.

---

### Post by Jonathan Precise on 2013-08-27
Press Ctrl. Alt. F1

Enter your username and password.

Then type:

```
sudo apt-get install ubuntu-software-center gnome-terminal unity ubuntu-branding ubuntu-desktop
```

Then type in:

```
sudo lightdm
```

If any error messages appear, post them here.

---

