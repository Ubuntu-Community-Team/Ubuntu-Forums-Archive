---
title: "add/remove applications"
date: 2008-08-11
forum: New to Ubuntu
---

### Post by Gumpers on 2008-08-11
I have ubuntu 8.04 desktop edition loaded on my computer, I have a problem with the add/remove application when it comes up on my monitor the application stretches off the right hand of the screen and i can't read all of the message or see the scroll bar. Is their a fix for this problem? I am a new user to ubuntu.
Thanks for any help, Gumpers.

---

### Post by tuxxy on 2008-08-11
Can you not just resize the window?

---

### Post by nvteighen on 2008-08-11
Some questions:
1. Does this happen to other applications too?
2. Have you Desktop Effects enabled? (System->Preferences->Theme)
3. Have you changed configuration related to font rendering or screen resolution?

OK, if you answer these three questions with "Yes!", then try disabling Desktop Effects, restart X Server (Ctrl+Alt+Backspace, save any open work before doing this) and see if it's solved. 

Tell us the results or ask if you have any doubt.

---

### Post by iv2101 on 2008-08-11
If you right-click on the button that appears on the panel when you open the add/remove window, there will be options to change size. Try maximizing this window.
You can move a window by pressing Alt and grabbing any part of the window with the mouse.

---

### Post by Gumpers on 2008-08-11
> **iv2101 said:**
> If you right-click on the button that appears on the panel when you open the add/remove window, there will be options to change size. Try maximizing this window.
You can move a window by pressing Alt and grabbing any part of the window with the mouse.

Evidently the window was maximized if i right click on button and unmaximize the window i gan grab the window and move it to the left and get the other third of the window but then the right side is hidden. Although with the window maximized i can not grab the window and move it. I dont understand that?

---

### Post by SunnyRabbiera on 2008-08-11
add/ remove is very simplistic anyway, its good for beginners but is not the best tool for regular use.

---

### Post by Gumpers on 2008-08-11
> **nvteighen said:**
> Some questions:
1. Does this happen to other applications too?
2. Have you Desktop Effects enabled? (System->Preferences->Theme)
3. Have you changed configuration related to font rendering or screen resolution?

OK, if you answer these three questions with "Yes!", then try disabling Desktop Effects, restart X Server (Ctrl+Alt+Backspace, save any open work before doing this) and see if it's solved. 

Tell us the results or ask if you have any doubt.
I did the Ctrl+alt+backspace, is that the same as a reboot? I am not sure how to go about disabling desktop Effects. Thanks, Gumpers

---

### Post by Riffer on 2008-08-11
Please tell us your video card, monitor and resolution.  Also tell us if you have Compiz enabled.

---

### Post by Gumpers on 2008-08-11
> **tuxxy said:**
> Can you not just resize the window?

Window will not resize to fit screen. Thanks, Gumpers

---

### Post by Gumpers on 2008-08-11
> **Riffer said:**
> Please tell us your video card, monitor and resolution.  Also tell us if you have Compiz enabled.

vido card is on board mainboard it is biostare k8m800 micro am2
resolution is 640x480. monitor is dell crt quit old. Thanks, Gumpers

---

### Post by Riffer on 2008-08-11
From the drop down menus go to System > Preferences > Screen Resolution.  Try changing the setting to something like 1024 x 768 or higher.

If you put your mouse pointer over the desktop and right click up will come a context menu.  At the bottom is "Change Desktop Background", click on that.  There should be a tab named Visual Effects, click on that.  Compiz is enabled if any of the bottom 2 radio buttons is marked.

---

### Post by nvteighen on 2008-08-12
> **Gumpers said:**
> I did the Ctrl+alt+backspace, is that the same as a reboot? I am not sure how to go about disabling desktop Effects. Thanks, Gumpers
Ctrl+Alt+Backspace resets the "X server", the graphical system. It's a useful thing when a graphical program crashes and you can't kill it manually for some reason; this way, you don't have to reboot your computer. Also it's used when changing some configuration details that require to restart X.

---

