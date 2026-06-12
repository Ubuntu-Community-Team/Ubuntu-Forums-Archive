---
title: "How do I reset xorg.conf?"
date: 2008-10-17
forum: New to Ubuntu
---

### Post by Dorrax on 2008-10-17
I want to disable my touchpad. I have qsynaptics, but when I run it, it keeps telling me to set SHMConfig to true, I've done that, but it still doesn't work. I've tried rebooting, ctr-alt-f1, nothing seems to reset X11. How do I do it, step-by-step?

Thank you

---

### Post by NullHead on 2008-10-17
You can redo the xorg.conf like so: ```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by jerome1232 on 2008-10-17
edit: Beaten to it!

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Then restart X (ctrl+alt+backspace) or sudo /etc/init.d/gdm restart

---

### Post by NullHead on 2008-10-17
> **jerome1232 said:**
> edit: Beaten to it!

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Then restart X (ctrl+alt+backspace) or sudo /etc/init.d/gdm restart

Well you're correct. I forgot the "-phigh" in mine. Thanks for posting it anyways :)

---

### Post by gn2 on 2008-10-17
Enter ```
sudo gedit /etc/X11/xorg.conf
``` in a terminal.

Your xorg.conf will open in gedit the text editor.

Add # signs to the start of the section for your synaptic touchpad so that the section looks like this:

```
#Section "InputDevice"
#	Identifier	"Synaptics Touchpad"
#	Driver		"synaptics"
#	Option		"SendCoreEvents"	"true"
#	Option		"Device"		"/dev/psaux"
#	Option		"Protocol"		"auto-dev"
#	Option		"HorizEdgeScroll"	"0"
#EndSection
```

Save it then Ctrl+Alt+Backspace to log out, log in again and hopefully your touchpad should be disabled.

---

### Post by Dorrax on 2008-10-18
None of those work. the dkpg-reconfigure did get me a fresh xor.conf, which was good because the # thing messed up my moniter. I want to install q synaptics, and I'm following the instructions I find, but nothing works, I can't get the SHMConfig to set to "true".

---

### Post by phidia on 2008-10-18
Have you tried the method provided by gn2 in post #5 here? What was the result from that?

You can also use nano in place of gedit.

---

### Post by Xiong Chiamiov on 2008-10-18
> **gn2 said:**
> Enter ```
sudo gedit /etc/X11/xorg.conf
``` in a terminal.


Tsk, tsk, don't teach bad habits.  When launching a GUI app, [use gksudo instead]("http://www.psychocats.net/ubuntu/graphicalsudo").

---

### Post by gn2 on 2008-10-18
> **Xiong Chiamiov said:**
> Tsk, tsk, don't teach bad habits.  When launching a GUI app, [use gksudo instead]("http://www.psychocats.net/ubuntu/graphicalsudo").

Nah, Alt+F2 for GUI apps! ;)  

(my bad for not using gksudo, hangs head in shame, should really know better)

---

### Post by Dorrax on 2008-10-19
I tried the method in #5, it messed up my screen. Had to reset the xorg.conf using the method in #3 to fix it.

---

