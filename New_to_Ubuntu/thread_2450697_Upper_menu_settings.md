---
title: "Upper menu settings"
date: 2020-09-18
forum: New to Ubuntu
---

### Post by j-o-e-l on 2020-09-18
Hi all,
I'm new to Ubuntu (using it for about four months).
I currently use Zoom for my work, and I noticed that when I exit from the program, the program does not close: an icon for Zoom appears in the top right corner, and it remains open. I would rather no program have this ability, as I personally don't like it.
I've been searching for how to disable this for the last half an hour, to no avail. I tried downloading Tweaks, and searched through the settings for Zoom and Ubuntu. 
Any ideas for how to remove this thing?
Thank you!

---

### Post by CelticWarrior on 2020-09-18
Welcome.

There are no system-wide settings for what you want.
Problem "solved". You can stop looking for it now.

---

### Post by j-o-e-l on 2020-09-18
That's frustrating! But thank you!

---

### Post by CelticWarrior on 2020-09-18
You're welcome.

I should have added that there aren't such settings in any OS under the sun. If any software keeps running in the background it will.

---

### Post by j-o-e-l on 2020-09-18
Right. I had disabled it on Discord using my Windows machine, but it was through a setting on Discord itself. I was hoping there was some way to make a program exit when I press the X in the right corner of the program's window, like most programs do (and all of my other programs on Ubuntu do).
I'm new to this, though, so I'm still understanding how to phrase these questions and deal with the issues.

---

### Post by tea for one on 2020-09-18
You mentioned that the Zoom icon is in the top right of the panel - this could be the indicator section with an applet.

Perhaps try **right click** to see if there is a **Quit/Close** option?

---

### Post by j-o-e-l on 2020-09-20
Thank you! Yes, there is that option. I was hoping to make it not appear there at all, but I understand that it is not possible. I read one work-around: to create a hotkey that simply ends Zoom. I will probably do that.

---

### Post by Impavidus on 2020-09-20
Some background that you may (or may not) find interesting.

There are two basic ways to exit a program. The first is when the program calls the _exit() system call, which is a request by the program itself to terminate. The OS will then terminate the program. The second is when the program receives a signal that's neither handled nor ignored, like when you kill a program.

Clicking the X on the window of the program is neither of that. Clicking the X makes the window manager send a request to the program to close that particular window and the program is free to interpret that request in any way it likes. Some programs have multiple windows open at the same time, some (actually, most) have no window at all and some programs are command line tools that, on user request, open a window to show some graphical output and close the window when the user asks, either by command or by hitting a key while the window is in focus or by clicking the X. I sometimes make such tools, as it's much easier to write programs with graphical output than with graphical input.

---

### Post by j-o-e-l on 2020-09-20
Thank you! Well-put. This is food for thought for me.

---

