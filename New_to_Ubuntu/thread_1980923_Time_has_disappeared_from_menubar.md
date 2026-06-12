---
title: "Time has disappeared from menubar"
date: 2012-05-16
forum: New to Ubuntu
---

### Post by jcse7en on 2012-05-16
Hi there

I hope not a silly question but the time has suddenly vanished from the menu bar in the upper right hand corner of my screen.

I've searched online for remedies but have failed.

I went on dconf editor but it the datetime option is not on there so I've obviously deleted/switched something off.

Any help will be much appreciated.

Thanks in advance

JC

ps I'm using ubuntu 12.04 by the way - thanks

---

### Post by jtarin on 2012-05-16
Alt + Right-click on panel, choose add to panel. A selection dialogue will come up with a listing of applets to install in the panel. Choose the "Notification Area" applet.

---

### Post by jcse7en on 2012-05-16
> **jtarin said:**
> Alt + Right-click on panel, choose add to panel. A selection dialogue will come up with a listing of applets to install in the panel. Choose the "Notification Area" applet.

Thanks for replying but unfortunately alt right click doesn't work...

---

### Post by cortman on 2012-05-16
Press the Super key (most keyboards show a windows logo on it) and type "clock". Select the Time and Date application, go to the clock tab, and make sure "Show a clock in the menu bar" is selected.
This assumes you're running Unity, which by your previous posts seems to be the case.

---

### Post by jcse7en on 2012-05-16
> **cortman said:**
> Press the Super key (most keyboards show a windows logo on it) and type "clock". Select the Time and Date application, go to the clock tab, and make sure "Show a clock in the menu bar" is selected.
This assumes you're running Unity, which by your previous posts seems to be the case.

Thanks again but I did all that and still nothing is happening. Yes I am running Unity.

---

### Post by cortman on 2012-05-16
> **jcse7en said:**
> Thanks again but I did all that and still nothing is happening. Yes I am running Unity.

Ok, in a terminal run

```
sudo apt-get install indicator-datetime
```

To make sure it's still installed.

---

### Post by jcse7en on 2012-05-16
> **cortman said:**
> Ok, in a terminal run

```
sudo apt-get install indicator-datetime
```

To make sure it's still installed.

Thanks Cortman that did it!!!!!

Much, Much, Much apreciated!!!!:P

---

### Post by cortman on 2012-05-16
> **jcse7en said:**
> Thanks Cortman that did it!!!!!

Much, Much, Much apreciated!!!!:P

You're quite welcome. Glad it was that simple. :)
Mark the thread [SOLVED] if you would, using the thread tools in the upper right.
Thanks, and good luck!

---

