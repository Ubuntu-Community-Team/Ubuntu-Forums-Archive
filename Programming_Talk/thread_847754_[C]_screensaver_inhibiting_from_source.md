---
title: "[C] screensaver inhibiting from source"
date: 2008-07-02
forum: Programming Talk
---

### Post by JupiterV2 on 2008-07-02
I have the source for a program I use quite a bit. It is the only one I have which does not inhibit the gnome screensaver from activating. I know that I can run a script to inhibit the screensaver during a terminal session (gnome-screensaver-command -i) but I'd like to do this from within the code. I would imagine that CPU priority level has little to do with it. What can I do to tell gnome that the program is active and receiving output so it doesn't need to activate the screensaver.

---

### Post by odyniec on 2008-07-04
This is surely not the best way to do this, but, since you already know the command that does what you need, you can simply call it from within your code using system(). The gnome-screensaver-command man page says that the "-i" option blocks execution of the program, so you'll probably need to call it in a forked child process, eg. something along the lines of:
```
if (pid = fork()) {
    system("gnome-screensaver-command -i");
}
```

---

