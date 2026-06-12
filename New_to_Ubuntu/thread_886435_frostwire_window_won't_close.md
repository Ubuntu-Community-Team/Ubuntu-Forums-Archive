---
title: "frostwire window won't close"
date: 2008-08-11
forum: New to Ubuntu
---

### Post by Matt26 on 2008-08-11
is there a way that i can make a frostwire window on my desktop close when it isn't responding?  i have already gone into System Monitor,Processes and killed the Frostwire application however the window still remains and everytime i click on the close button nothing happens.  any ideas?  thanks.

---

### Post by anotherdisciple on 2008-08-11
hmmm... have you tried opening the terminal and typing...

```
killall frostwire
```

...?

Also... if you are using ubuntu... you can add an applet to your gnome panel called "Force Quit"... that should do the same thing.

---

### Post by ginnie6 on 2008-08-11
do you have downloads that haven't finished? I found that I had to clear all downloads whether they were active or not before Frostwire would shut down.

---

### Post by tom66 on 2008-08-11
If the above command does not work, try using 'xkill' from a terminal, then click on the non-responding application.

---

### Post by speedup on 2008-08-12
I also have the same problem, I already executed the killall frostwire and still the frostwire still exist.

What's weird is when we run ps aux | grep frostwire there appeared grep frostwire. Should it be doing that?

---

### Post by Matt26 on 2008-08-13
> **tom66 said:**
> If the above command does not work, try using 'xkill' from a terminal, then click on the non-responding application.

this worked for me, although not right away.. i can't recall the exact process that occured but i clicked on the frostwire window after being prompted by xkill to click on the window that i wanted to kill, but when i did that my screen seemed to refresh and my window layout on the taskbar at the bottom of the screen seemed to shift position, then a new window appeared in the taskbar with some garble appearing as the window title, and when i clicked on that my frostwire window went away and all was well again- weird..

---

