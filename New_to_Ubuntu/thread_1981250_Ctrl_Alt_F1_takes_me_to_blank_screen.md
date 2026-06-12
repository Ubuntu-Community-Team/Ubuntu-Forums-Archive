---
title: "Ctrl Alt F1 takes me to blank screen"
date: 2012-05-16
forum: New to Ubuntu
---

### Post by frohfroh on 2012-05-16
I am not sure if that is right, but reading other topics I got the impression that pressing Ctrl+Alt+F1 (or F2,F3 ... F6) should get me to a terminal, what would be handy considering the amount of crashes in which LibreOffice gets me.
However when I try any of them I only get a blank screen. Any suggestions?
P.S.: I saw some threads about issues close to this one, and sometimes apparently the video card matters. Mine's an integrated Intel.

---

### Post by Gone fishing on 2012-05-16
Just to make sure its not working  and not just off the screen just click enter a few times and see if the cursor appears.

---

### Post by frohfroh on 2012-05-16
No, definitely not that. I forgot to mention that by using Ctrl Alt F7 I do get back to the desktop

---

### Post by dolphin194 on 2012-05-16
What type of monitor are you using? Chances are that your monitor may be unable to display the resolution used by the command line.

---

### Post by hakermania on 2012-05-16
Hey, are you sure that in this black screen, in the top left there aren't any letters requesting for your username?

It is a 'full screen terminal', not a normal one...

---

### Post by pqwoerituytrueiwoq on 2012-05-16
type your user name then press enter then type your password and press enter
if the screen is still blank hold a letter for a few seconds
if part of the display is off screen it should show up

---

### Post by frohfroh on 2012-05-17
Thanks for the answers.
It's a laptop, I'm using its screen, how can I know if it supports the resolution?
Tried all the rest, nothing worked. I tried also a sudo reboot + Enter + password + Enter to see if something happened and nope...

---

### Post by gastonius.lagaffus on 2012-09-01
I ran into the same problem and judging from what I read on some other sites, it could be an issue with the nvidia driver. The easy fix is disabling all fancy gfx-console stuff in GRUB (don't worry, X will continue to work fine)


[LIST=1]
[*]open '/etc/default/grub' (use sudo or you won't be able to save)
[*]uncomment the 'GRUB_TERMINAL=console' line
[*]run 'sudo update-grub' from a console
[*]reboot
[/LIST]
These steps fixed the problem for me, I hope they work for you.

---

