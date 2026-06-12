---
title: "Bash Dialog?"
date: 2008-09-03
forum: Programming Talk
---

### Post by chris062689 on 2008-09-03
I've been looking into Bash programming, and wanted to see how to make the text-based GUI's seen in the Debian (and Ubuntu Alternative) installer.
(ex: [http://www.aurel32.net/info/debian_arm_qemu_di_language.png](http://www.aurel32.net/info/debian_arm_qemu_di_language.png))
After googling, they said it used "dialog", but when I attempt to use it, it gives this:
```

chris@chris-desktop:~$ dialog
The program 'dialog' is currently not installed.  You can install it by typing:
sudo apt-get install dialog
bash: dialog: command not found

```

But I've seen such dialogs before even when installing programs with synaptic, so I assume it's just called by another name?

---

### Post by mssever on 2008-09-03
Usually those programs use ncurses for that. Isn't dialog a bash front-end to ncurses? I'm not on Linux at the moment, so I can't check. At any rate, if the language being used has ncurses bindings, then there probably is nothing extra you have to install. Since bash doesn't have ncurses bindings, it's not surprising that you have to install a separate program to use ncurses.

---

