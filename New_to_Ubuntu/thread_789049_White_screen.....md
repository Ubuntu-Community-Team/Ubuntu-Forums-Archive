---
title: "White screen...."
date: 2008-05-10
forum: New to Ubuntu
---

### Post by 2weird on 2008-05-10
Hi, I have recently installed kubuntu 8.4 and everything was going great until I installed the desktop effects thing and compiz and set the effects to exta. Now my screen has turned white yet the 3d desktop works:confused:.
I am writing this in the failsafe mode where I ran firefox from the terminal.
How can I get my desktop back to normal?
Please take into consideration that I have no clue about the commands in terminal.
Thank you.

edit: Just for your information, I have an extremly decent pc, running 2gb ram, dual core 2.00GHz each, ATI Radeon x1600 series 512MB RAM.

---

### Post by Freddy on 2008-05-10
Can you use the "Run Command" box? If so, write 'kwin --replace' in the box that should appear. Now reboot and hopefully you will have a functioning KDE again.

This will of course make KDE use kwin as the window manager instead of Compiz.

---

### Post by 2weird on 2008-05-10
that only worked in failsafe mode.
When logging as default or kde the screen is still white.
Is there a way I can call the desktop effects menu from the terminal?

---

