---
title: "No Menu Bars. Help!!!"
date: 2008-11-10
forum: New to Ubuntu
---

### Post by Robertorps on 2008-11-10
Hi, I've been using ubuntu for a while now, and this problem never happened before:

After upgrading to Intrepid, and installing all upgrades, menu bars disappeared. Tried reinstalling Ubuntu 8.04 and also installed all updates and the bars are no where to be seen!

I managed to open a terminal find my way to get the basic stuff done, but this is not a nice way to work. Is there something I could do?

---

### Post by lswest on 2008-11-10
Can you post a screenshot?  I'm not sure I know what you mean. (Just hit the Print Screen key)

---

### Post by Robertorps on 2008-11-10
Here it is:

I also tried adding new menu bars, but the option does not appear.

---

### Post by simtaalo on 2008-11-10
try moving your mouse pointer to the top of the screen and right-click and see if you can "add panel" and see if that works.

EDIT: just seen you tried that and didnt work. i had a similar problem recently, try looking here and see if it helps [http://ubuntuforums.org/showthread.php?t=973174](http://ubuntuforums.org/showthread.php?t=973174)

---

### Post by Robertorps on 2008-11-10
It is exactly my problem. Thanks a lot man for that wuick responses. I'll try to fix it (at the end of the thread the basically ask to reinstall gnome desktop).

---

### Post by Coreigh on 2008-11-10
I am not sure about the syntax here but:
```
sudo dpkg -i --reconfigure gnome-panel
```

---

### Post by Robertorps on 2008-11-10
I'll give it a try. I have to go for an hour, but I'll psot as soon as I come back to check. Thanks!!!

---

### Post by Chris Edgell on 2008-11-10
If it's wrong for me to post the solution that worked for me , someone please tell me.  (Once I read that just because something worked for me doesn't mean it pretains to someone elses situation.)

 Re: More about lost menu bar
try pressing the alt-f2 keys...see if it brings up a run dialog box.

if it does, type the following into it:

Code:

xfce4-panel &

that should give you the top panel. if no bottom panel appears...right click somewhere in an empty spot of the top panel and choose "new panel".

hope that helps.

---

### Post by Coreigh on 2008-11-10
Chris, its not wrong to post your solution, but it is always good to "qualify" it and say "This is what worked for me ..." or some such thing. Everybodies system is a little different. In your case it looks like you were using the Xfce window manager (like Xubuntu) as opposed to Gnome ... BUT it does look like the same solution.

---

### Post by simtaalo on 2008-11-10
its not a bad thing to write whats worked for you. of course your solution is dependant on the OP running xfce. from the screenshot it looked like gnome, but i couldnt say for sure.

which is also a good reason people to clearly outline what they are running so people can give advice based on that.

---

### Post by Robertorps on 2008-11-10
Alt F2 does not work.

---

### Post by Robertorps on 2008-11-10
People have told me this issue appears when one wants to get rid of Evolution (the why is still not clear...) what people have suggested is to reinstall gnome desktop or the dpkg command).

---

### Post by Ryadt on 2008-11-10
Try ```
sudo apt-get install gnome-panel
``` and see if it fix it.

---

### Post by Robertorps on 2008-11-10
I just saw your message after trying another solution from another thread:

Reinstalling gnome-desktop.

I am just wondering if I will have two copies of ubuntu-dektop on my laptop. If that is the case, is there a way to remove one of them?

---

### Post by Ryadt on 2008-11-10
You can't have 2 gnome-desktops. The  gnome-desktop is just a package that contains information about the original ubuntu environment. It is not the actual desktop.

---

### Post by Robertorps on 2008-11-11
After installing ubuntu-desktop the task bars are on the screen again!! :D

Thanks a lot to everyone for their answers.

---

