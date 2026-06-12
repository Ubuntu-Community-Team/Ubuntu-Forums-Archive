---
title: "How to copy and paste in xterm 14.04 unity"
date: 2014-06-14
forum: New to Ubuntu
---

### Post by johnsmithbattlenet on 2014-06-14
I really don't understand why something like this is so complicated, and it really turns me off to linux.  I cannot find any method of pasting into the xterm terminal.  I don't know why a built terminal supposedly for newcomers to linux would be so difficult.   ctrl shift v, ctrl v, right click, and  middle mouse click doesn't work.  The insert hotkey is not possible as my laptop (c720) doesn't have insert.    I will install another terminal if required, but rather just use the default tools given.  Does anyone have any idea of how to do this?

---

### Post by Impavidus on 2014-06-15
The xterm isn't particularly smart, but even there select -> click with middle mouse button/mouse wheel works (just as shift-insert). The other terminals, like gnome-terminal, are smarter. There the middle mouse button, the menu, the right click context menu, ctrl-shift-v and shift-insert (but not ctrl-v) should all work. More advanced terminals than xterm should be installed by default: gnome-terminal on Ubuntu, xfce4-terminal on Xubuntu, konsole on Kubuntu, ... These are the default terminals, xterm is provided for compatibility or backup. In unity, try opening a terminal by searching for "terminal", not "xterm".

---

### Post by The Cog on 2014-06-15
They do work. 

Bear in mind that there are two separate copy/paste buffers. There's one copy/paste buffer that that you put text into by highlighting some text and doing right-click/Copy or Ctrl-Shift-C (This is Ctrl-C in most applications, but Ctrl-C has other meanings in the terminal). You paste from this buffer with right-click/Paste or Ctrl-Shift-V (Ctrl-V in most apps). This is the kind of copy/paste you are used to in windows.

Then there is the X copy/paste buffer that simply remembers the last bit of text you highlighted and pastes that when you use middle-click. 

Loading the first, windows-like buffer inevitably also loads the X buffer because it involves highlighting text, which can give the impression that there is only one buffer. If you want to work with two separate paste buffers, you must load the windows-like buffer first and then load something else into the X buffer by highlighting that. The X buffer cannot be used to replace text because highlighting the text top replace reloads the X buffer, so you have to use the windows-like buffer for that.

Oh, one difference to windows: The buffer contents are lost when the source window is closed. Don't close the window you are copying from until you have finished pasting.

---

### Post by buzzingrobot on 2014-06-15
> **johnsmithbattlenet said:**
> ...  I cannot find any method of pasting into the xterm terminal.  I don't know why a built terminal supposedly for newcomers to linux would be so difficult....

While you are probably refering to the Gnome Terminal used in Ubuntu, Xterm was not created for "newcomers". It's the original terminal emulator for the X Window System that Linux GUI's are built on, dating back to 1984.

---

### Post by johnsmithbattlenet on 2014-06-15
> **buzzingrobot said:**
> While you are probably refering to the Gnome Terminal used in Ubuntu, Xterm was not created for "newcomers". It's the original terminal emulator for the X Window System that Linux GUI's are built on, dating back to 1984.

I meant that ubuntu itself is good for newcomers and would think that it should come with a better terminal.  Apparently that is the case, as Impavidus said my version should come with gnome-terminal, yet I don't have it.  So, I've gotten the wrong impression.  I guess there's some issue with crouton not installing it on my chromebook or something, because it didn't come by default for me.

But thanks for the responses, I'll try what was said or otherwise download a different terminal.

---

### Post by GrouchyGaijin on 2014-06-15
I usually use terminator ;)

---

