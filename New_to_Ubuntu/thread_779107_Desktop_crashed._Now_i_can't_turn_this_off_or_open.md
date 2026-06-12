---
title: "Desktop crashed. Now i can't turn this off or open applications menu amongst others"
date: 2008-05-02
forum: New to Ubuntu
---

### Post by gottabeandrew on 2008-05-02
I opened the desktop folder and it said the desktop had crashed so i chose to end the application and now i can't click on any of the buttons on the taskbar or the bar with applications, places, system on. if i hold down the turn off button, the computer completely breaks and needs re-formatting every time so i can't do that. How can i get out of this?

---

### Post by eriqjaffe on 2008-05-02
Don't know how to fix the desktop, but you can still shut down / reboot your system gracefully.

CTRL-ALT-F1 will bring you to a virtual terminal.  Log in there (you won't see any visible feedback when you type your password, BTW) and enter the following at the prompt:

```
sudo shutdown -h
```

To reboot, change the "-h" to "-r".

Again, you'll be prompted for a password - same as before, you'll get no visual confirmation that you're typing anything, but that's by design.

---

### Post by fraser_m on 2008-05-02
Ctrl+Alt+Backspace

Restarts X.

Might work...

---

### Post by gottabeandrew on 2008-05-02
> **eriqjaffe said:**
> Don't know how to fix the desktop, but you can still shut down / reboot your system gracefully.

CTRL-ALT-F1 will bring you to a virtual terminal.  Log in there (you won't see any visible feedback when you type your password, BTW) and enter the following at the prompt:

```
sudo shutdown -h
```

To reboot, change the "-h" to "-r".

Again, you'll be prompted for a password - same as before, you'll get no visual confirmation that you're typing anything, but that's by design.

now I'm having to use these forums from my iPod. How do I get out of the virtual console thin and back to ubuntu? Also, I done what you said and now it says "shutdown: time expected. Try 'shutdown --help' for more information.". What should I do now?

---

### Post by eriqjaffe on 2008-05-02
> **gottabeandrew said:**
> now I'm having to use these forums from my iPod. How do I get out of the virtual console thin and back to ubuntu? Also, I done what you said and now it says "shutdown: time expected. Try 'shutdown --help' for more information.". What should I do now?To get back to the GUI, it's CTRL-ALT-F7.

Sorry, try:

```
sudo shutdown -t 0 -h
```

The "-t 0" sets the timeout to 0 seconds.  Then again, now that I think about it, you might just be able to do...

```
sudo poweroff
```

...as well.

---

