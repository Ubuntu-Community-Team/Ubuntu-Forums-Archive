---
title: "screen lock doesn't work"
date: 2012-09-11
forum: New to Ubuntu
---

### Post by samalaa on 2012-09-11
Hi everyone .
I'm using ubuntu 12.04 LTS .
The screen lock doesn't work , whenever I click on lock screen my screen freezes and turns to white , but the mouse keep moving, the same thing occurs when I click suspend .
It is set to lock screen on suspend .
so how can I fix this problem.

Thanks in advance .

---

### Post by ptosiani on 2012-09-11
> **samalaa said:**
> Hi everyone .
I'm using ubuntu 12.04 LTS .
The screen lock doesn't work , whenever I click on lock screen my screen freezes and turns to white , but the mouse keep moving, the same thing occurs when I click suspend .
It is set to lock screen on suspend .
so how can I fix this problem.

Thanks in advance .
Do you get the same behavior if you try to suspend using the console? 

Try to open a terminal with crtl + alt + t

and run: ```
sudo pm-suspend
```

---

### Post by samalaa on 2012-09-11
I tried sudo pm-suspend it suspended but it didn't lock the screen I do need the screen to be locked .
Thanks for your help

---

### Post by ptosiani on 2012-09-11
Try to implement this:

is a workaround to use a python script to lock the screen.

[http://www.howtogeek.com/61836/how-to-turn-off-your-monitor-with-a-hotkey-in-ubuntu/](http://www.howtogeek.com/61836/how-to-turn-off-your-monitor-with-a-hotkey-in-ubuntu/)

---

### Post by ptosiani on 2012-09-11
If you changed the Ubuntu screensaver, that may cause a problem, just to make sure you can try this: 

```

sudo apt-get remove xscreensaver xscreensaver-data-extra xscreensaver-gl-extra
sudo apt-get install gnome-screensaver

```

And then go back into the Keyboard configuration window, delete your custom shortcut, and reassign Ctrl+Alt+L to the Lock screen option under System.

This is the full post: 
[http://www.howtogeek.com/114027/how-to-add-screensavers-to-ubuntu-12.04/](http://www.howtogeek.com/114027/how-to-add-screensavers-to-ubuntu-12.04/)

---

### Post by samalaa on 2012-09-12
Thanks a lot it worked , actually this problem occurred after insatlling the xscreensaver but I didn't know how to fix it . Thanks again

---

### Post by samalaa on 2012-09-12
it stoped working again !! what should I do

---

### Post by raelgc on 2013-04-10
Disabled VSync on Unity/Compiz. I don't know how to do it, cause I use KDE. But I have a NVIDIA card, and I read in other posts that disabling will work. And it worked for me with KDE.

---

