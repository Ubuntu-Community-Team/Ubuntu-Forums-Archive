---
title: "Serious Problem Updating Ubuntu OS"
date: 2008-08-19
forum: New to Ubuntu
---

### Post by tobhiyah79 on 2008-08-19
I was updating my Ubuntu OS when the power of my laptop went out. Only 6% of installation remained. When I turned my laptop back on it booted up to the point where I enter my username and password. After entered the laptop screen goes blank!! I can only see and move the mouse...

What should I do???

Is there a way to boot or reboot the laptop in a previous saved state or version?

---

### Post by meanburrito920 on 2008-08-19
ouch. generally you probably want to plug in your laptop when upgrading. I'd back up your home directory and do a clean install.

---

### Post by Mizutsuki on 2008-08-19
> **tobhiyah79 said:**
> I was updating my Ubuntu OS when the power of my laptop went out. Only 6% of installation remained. When I turned my laptop back on it booted up to the point where I enter my username and password. After entered the laptop screen goes blank!! I can only see and move the mouse...

What should I do???

Is there a way to boot or reboot the laptop in a previous saved state or version?

Try this:
When it gets to a the blank screen try hitting ctrl-alt-F1.  If that takes you to a terminal you might be able to recover without a complete reinstall.

---

### Post by meanburrito920 on 2008-08-19
if you can get to a terminal, try running the command startx. If it fails, post the error message here

---

### Post by tobhiyah79 on 2008-08-20
I hit ctrl-alt-F1 and the screen goes black.... thats it....  What can I do?

---

### Post by meanburrito920 on 2008-08-20
reboot. when grub comes up, boot into recovery mode. tell us if that works.

---

### Post by Mizutsuki on 2008-08-20
> **tobhiyah79 said:**
> I hit ctrl-alt-F1 and the screen goes black.... thats it....  What can I do?

Are you saying the screen changes color, but no text appears?  You might try moving around ctrl-alt-F2 and such and see what happens.

---

### Post by tobhiyah79 on 2008-08-20
I can get into recovery mode. It give me a few options which I chose 7.10 (recovery). The screen goes into 4 options:

1. resume normal boot
2. repait broken packages
3. drop to root shell prompt
4. try to fix x server

The first two do not help. I do not know what to do with option 3and 4. What do you suggest?

---

### Post by meanburrito920 on 2008-08-20
Try #4. it should be what you want. have you tried #2? it should also help.

---

### Post by tobhiyah79 on 2008-08-20
Neither is working. At this point I just want to wipe the whole thing and start with a new installation from CD. (all my files are on an external) Is that possible?

---

### Post by meanburrito920 on 2008-08-20
Yes, you could do this. If all your files are external, then there should be no problem, and as an added bonus your computer should run faster afterwards. Just make sure you have all your important files on external media first.

---

