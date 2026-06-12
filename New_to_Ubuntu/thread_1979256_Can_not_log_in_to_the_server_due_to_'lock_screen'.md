---
title: "Can not log in to the server due to 'lock screen'"
date: 2012-05-13
forum: New to Ubuntu
---

### Post by AndyCanfield on 2012-05-13
Installed Ubuntu 12.04 Server yesterday.Now, whenever I boot, once i get past grub, it goes to a 'lock screen'. I call it the lock screen because I can't get out of that screen and to the console login prompt. I've tried every key on the keyboard, plus Ctrl+C, and nothing gets me to the login prompt. The only way I can get a shell is to SSH in through the LAN from another computer.

The lock screen shows "Ubuntu 12.04" and four dots which change color between red and white.

Ideally, how do I prevent that lock screen from coming up at all? Or, barring that option, how do I get off of that lock screen and back to the system console?

---

### Post by joetait on 2012-05-13
If you just want to get to a console screen, try ctrl+alt+F1. There are six tty's, ctrl+alt+F(1-6), and ctrl+alt+F7 is the graphical one. This is for the desktop though, so if it is different for server then sorry, I won't be much help

---

### Post by llamabr on 2012-05-13
I'm not too sure.  Maybe a screen shot would help.

Remember that you should be able to ctrl-alt f2 to get a console.  If you're running your server headless, you might also try:

```
sudo apt-get remove gdm
```

---

### Post by Prescilla on 2012-05-13
> **joetait said:**
> If you just want to get to a console screen, try ctrl+alt+F1. There are six tty's, ctrl+alt+F(1-6), and ctrl+alt+F7 is the graphical one. This is for the desktop though, so if it is different for server then sorry, I won't be much help
+1
Yes this.

---

### Post by AndyCanfield on 2012-05-13
Thanks for the lead! Research shows ...

For # = 1 through 10, Ctrl+Alt+F# gives me a completely blank screen, except that Ctrl+Alt+F7 takes me back to the lock screen. Enter, and patience, gives me a login prompt. I guess that when I tested every key on the keyboard it must have gotten upset by all the other keys I hit before I hit Enter.

Thanks! Solved!

---

### Post by Lisiano on 2012-05-13
I wouldn't say it's solved. Maybe worked around but not solved.
> **AndyCanfield said:**
> The lock screen shows "Ubuntu 12.04" and four dots which change color between red and white.
I think that is not a lock screen but is the Ubuntu boot logo. Can you "Remove" it by pressing Escape? It should show some messages regarding the boot process, usually disk checks and starting services. Ubuntu Server shouldn't even _have_ X installed so it can't in theory have a lockscreen by default.

---

### Post by AndyCanfield on 2012-05-17
> **Lisiano said:**
> I wouldn't say it's solved. Maybe worked around but not solved.
Solved in the sense that I can get past that screen. A better 'solution' would be to not show that screen at all, but immediately show the login prompt.
> II think that is not a lock screen but is the Ubuntu boot logo. Can you "Remove" it by pressing Escape? It should show some messages regarding the boot process, usually disk checks and starting services. Ubuntu Server shouldn't even _have_ X installed so it can't in theory have a lockscreen by default.It showed nothing but the text "Ubuntu 12.04" and the four white dots. The dots kept changing from red to white to red again, proving that the system was not dead.

No, Escape did not get me off of that screen.

Why do you think that "lock screen" is defined as "XWindows"? To me, any screen that appears to be deliberately designed to lock the console is a lock screen. However, I used quotes around 'lock screen' in the title because I was not sure if it was designed to be a lock screen.

I admit now that it apparently is not deliberately designed to lock the console. However, the developers of this screen ought to have added text like "Press Enter for a login prompt". The very fact that the screen shows no instructions as to how to get off of that screen, and the screen on my computer ignores most keyboard input, is poor user interface design.

---

### Post by Lisiano on 2012-05-17
Yes, that screen is the bootlogo or splash or plymouth boot logo or whatever else you want to call it. And I just associate lock screens with X.

You can try booting and disabling the logo, while booting (If you don't see Grub, hold shift) press E and locate "quiet splash" and remove splash from it, or also remove quiet if you want a more verbose boot, if that works then to make it permanent, open /etc/default/grub as root using nano or vi (Or whatever else you fancy), find this line
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```
And change acordingly. Then just issue a 
```
sudo update-grub
```

---

