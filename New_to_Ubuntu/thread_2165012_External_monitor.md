---
title: "External monitor"
date: 2013-08-02
forum: New to Ubuntu
---

### Post by Chris_Torok on 2013-08-02
Hey guys, I have an inspiron 1545 running 13.04. I've got it hooked up to an external monitor, and have the monitor set as the main display in settings. Also, mirror display is turned off. However, whenever I close the lid on the laptop, it cuts off the monitor. I have it set to 'Do Nothing' when the lid is closed under power settings. Any ideas?

---

### Post by Vladlenin5000 on 2013-08-03
Don't close the lid? Sorry, I don't a have a solution either.

---

### Post by courseinmiracles2 on 2013-08-03
Yes but the monitor is getting it's source from the computer. I would agree with Vlad.

---

### Post by Bucky Ball on 2013-08-03
If you close the lid your computer is either in suspend or hibernate. You do not want to have it set to stay on while the lid is shut and don't know anyways to. As you're monitor is only reflecting what the computer is sending out, when you close the lid the monitor will go off as the computer has gone to sleep. It figures.

* Note: if you have a situation where you close the lid and the external monitor does stay on, if that is translated to the computer that would mean the laptop screen would be staying on when you close the lid. You definitely do NOT want that.

---

### Post by Chris_Torok on 2013-08-04
well i kind of do want the screen to stay on when i close it. see, this laptop is too old and beat-up to be used as a laptop anymore, so i'm turning it into a desktop. basically, once i get this thing the way i want it, it's never moving again. so i want it to take up as little space as possible.

---

### Post by ebyeby6 on 2013-08-04
I had a similar problem on a laptop. Two things I tried.

Turn on the laptop then immediately close the lid. Once the Ubuntu login screen or desktop starts up, the external monitor will fire up - no idea why this works!

If that doesn't work, the other solution is a bit more work. Install **arandr** from the software center. Then with your screens setup how you like, run arandr, click **Layout** menu and **Save**, putting the file in your home folder call it **fixscreen.sh** for example. Open a terminal window and type "**./fixscreen.sh**" but don't press enter yet. Then close the lid, and now press enter. If your external monitor comes to life, then you can add that file to the startup section in Ubuntu and it will run that script every time you boot. Just search the dash for Startup and you should find the section.

---

### Post by Chris_Torok on 2013-08-05
Haha that first thing totally worked! That saved a bunch of space on my desk. I might try that second option when I've got some more time, however, it might be kind of pointless because my power button is under the lid, so I'd have to open it every time I wanted to boot it up lol. Thanks for the tips!

---

