---
title: "Ok, I have no idea what happened..."
date: 2008-07-01
forum: New to Ubuntu
---

### Post by Icarus001 on 2008-07-01
Okay, i was on my Ubuntu 8.04 desktop and by accident i pressed the keys <ctrl>+<alt>+<F9> and the computer went to a black screen with a small blinking white rectangle(I'm not sure what you'd call it)and nothing happened, so i powered down the PC and turned it back on and it will not go back to the boot screen...
As i mentioned above I'm running Ubuntu 8.04
Thanks to all who can help.

---

### Post by llama320 on 2008-07-01
When you say it doesn't go back to the boot screen, how far do you get? Does the splash screen come up? Grub?

Also, however far you get, try ctrl+alt+F7 (which brings you back to X) when you get there

(for more on what X is.. [http://en.wikipedia.org/wiki/X_Window_System](http://en.wikipedia.org/wiki/X_Window_System))

Good Luck

---

### Post by luisito on 2008-07-01
After you pressed Ctrl-Alt-F9 you could have come back to your usual screen by pressing Ctrl-Alt-F7.

Whatever happened when you turned it off that is causing it not to reboot is independent of that. Can you describe what happens when you try to boot?

---

### Post by tjwoosta on 2008-07-01
ok the blank screen with the binking white square is a console

ctrl-alt-f7 should bring you from the console back to X

if you are stuck at a command line and cant get back to your desktop just do this command
```
startx
```

---

### Post by kuja on 2008-07-01
"ctrl + alt + f1-12" is how you switch both to virtual terminals (f1-f6) and to different x sessions (f7-f12). You could have gotten back to the desktop by pressing "ctrl + alt + f7" which is the default for an x session.

So now it won't even go in to the grub too loader? Do you get any error messages on the screen?

---

