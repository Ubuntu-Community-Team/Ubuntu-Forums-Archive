---
title: "External Monitor Resolution Trouble"
date: 2008-08-23
forum: New to Ubuntu
---

### Post by diego898 on 2008-08-23
I hooked up an external monitor and now the resolution is too big on it. What I mean is, the desktop is literally to big to fit on the monitor, so when I drag my mouse to the right, or to the top, etc, the screen drags as well to reveal the rest of my screen. For example, if I can see the top left of my desktop, in order to see the bottom right I have to drag the mouse towards the bottom right of the desktop. Then that piece of the desktop is revealed, but the top left is no longer visible.

This problem does NOT occur on my laptop's original screen. Is there anyway I can make it so it auto detects what screen its on and fix the resolution automatically?

---

### Post by overdrank on 2008-08-23
> **diego898 said:**
> I hooked up an external monitor and now the resolution is too big on it. What I mean is, the desktop is literally to big to fit on the monitor, so when I drag my mouse to the right, or to the top, etc, the screen drags as well to reveal the rest of my screen. For example, if I can see the top left of my desktop, in order to see the bottom right I have to drag the mouse towards the bottom right of the desktop. Then that piece of the desktop is revealed, but the top left is no longer visible.

This problem does NOT occur on my laptop's original screen. Is there anyway I can make it so it auto detects what screen its on and fix the resolution automatically?

Hi and what is the model of the graphics card? Have you tried to use the command using the alt, F2 keys and enter ```
gksu displayconfig-gtk
``` and setup your extra monitor there.

---

### Post by diego898 on 2008-08-24
I have an ATI Radeon X1400. Running that command, the dialog pops up. For that screen, does the monitor I pluged in count as Screen 1 or screen 2? I think screen 1. For model it sais plug n play and resolution is 1680 X 1050. What can I do to make the resolution automatically adjust when I plug in this monitor? Do I have to download the driver for the monitor?

---

### Post by diego898 on 2008-08-24
Can someone please help me with this? Its a very big inconvenience!

---

### Post by diego898 on 2008-08-24
It should be cleared up here: the monitor is not for a dual monitor setup. Its a plug n play setup where the laptop remains closed and this monitor essentially replaces it while it is connected. 


Please Help!

---

### Post by diego898 on 2008-08-24
Bump

---

### Post by diego898 on 2008-08-24
I have managed to get the desktop to now fit entirely on the desktop, but my maximum resoltion is 640 X 480. What can I do?

---

