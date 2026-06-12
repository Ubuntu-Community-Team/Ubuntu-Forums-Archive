---
title: "ctrl+Alt+F1 and no graphic interface again"
date: 2013-12-09
forum: New to Ubuntu
---

### Post by etielsolrac on 2013-12-09
After I pressed ctrl+alt+F1 I couldn't get the graphic interface again, even after reboting !...

thank you

---

### Post by deadflowr on 2013-12-09
Did you try ctrl + alt + F7 ?

---

### Post by etielsolrac on 2013-12-09
Yes, I did, then I did ctrl+alt+del.

---

### Post by deadflowr on 2013-12-09
I don't know which version of Ubuntu you are on, but try
```
sudo service lightdm restart
```
if on 12.04
or
```
sudo restart lightdm
```
if on 13.10(maybe 13.04, and 12.10, not sure about those two though)

Tells what happens then.

You'll need to login to a console session, the ctrl+alt+F1-6 sessions.

---

### Post by etielsolrac on 2013-12-09
Well, I'll  try those, thank you.

---

### Post by etielsolrac on 2013-12-09
It didn't work, I think it's the graphics driver that doesn't like my having two monitors.

---

### Post by deadflowr on 2013-12-09
> **etielsolrac said:**
> It didn't work, I think it's the graphics driver that doesn't like my having two monitors.
^^Possibly relevant information.
When did you add the second monitor?
And follow up what happens when you unplug the second one.

---

### Post by cborga1985 on 2013-12-09
What graphics card do you have?

---

### Post by etielsolrac on 2013-12-10
My graphics card is GeForce GT 540M  (NVIDIA compatible), I have a Qosmio with an external monitor.

---

### Post by etielsolrac on 2013-12-10
Everything was running smoothly before ctrl-alt-F1...

---

