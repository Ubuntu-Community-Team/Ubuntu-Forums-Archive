---
title: "Tabs in VIM"
date: 2006-07-08
forum: Programming Talk
---

### Post by mrvw0169 on 2006-07-08
Don't know if I should ask here, but I figured programmers would know VIM better.

I'm using VIM 7.0 and with it's tab feature (:tabe defs.h) it's very handy. I was just wondering if there's a way to specifically goto a tab (hitting gt goes by one by one) and if I can use the mouse to click on the tabs -- I read I had to set xterm-mouse somewhere... Currently, I can't click on the tabs in gnome-terminal. I know I could use gVIM, but I'm still more comfortable in the terminal.

Thanks!

---

### Post by yigal.weinstein on 2006-08-04
First here is my .vimrc file which lets me click on a desired tab to bring up  to document with my mouse

Second {count} gt moves you to the {count} tab.  So lets say you want the 3rd tab so :3gt will do it for you.

Third sorry for not replying sooner.  I just reinstalled Ubuntu over Debian and haven't been actively to these forums for a while.

Best

---

### Post by mrvw0169 on 2006-08-04
Ah, thanks for replying... I actually found out it was set mouse=a a little while ago so it's nice, but it was even better when I found out {count} tab on accident...

Thanks for your .vimrc - I actually have a problem now where I want to do the X highlight text in vim in an xterm + copy/paste Middle Mouse button from a terminal to say gedit... It just doesn't work as it switches the mode to visual -- sometimes it does work though if I yank the lines and somehow it gets copied when I hit the middle mouse button (not often it works though) so if you know a way to remedy this, it would be most helpful!

---

### Post by yigal.weinstein on 2006-08-05
I seem to have no problem using gnome-terminal + gedit + vim with my .vimrc and copying lines back and forth between them.  I highlight in vim it copies in visual but the copied material is "in" the memory area accessed by the middle button.  I must confess that I use a touchpad so my middle button is tapping the touchpad but it should work for a normal 3-button mouse.

My suggestion use my .vimrc and tell me if you can do what you want or tell me what fails and I am more than willing to help.

---

