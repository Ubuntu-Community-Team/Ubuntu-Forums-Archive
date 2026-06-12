---
title: "Switching in and out of Terminal Server Client"
date: 2008-11-12
forum: New to Ubuntu
---

### Post by smithwk2 on 2008-11-12
I am using my Ubuntu desktop to access a Windows PC.  How can I minimize the terminal server client window?  Right now, I have to close that out to get to anything else on my Ubuntu machine.  Thanks in advance for help on this matter.

---

### Post by Strawp on 2008-11-12
Same question. In 8.04, 7.10 and possibly 7.04 you could use ctrl+alt+enter to get hotkey control of your own desktop again and I'd use my keyboard combination to switch to a neighbouring desktop. I've managed this once under 8.10 but ctrl+alt+enter doesn't seem to work. The desktop switches (I get a glipse of the spinning cube animation) but the TSC window is always on top.

---

### Post by MockY on 2008-11-12
It sounds like you are running if full screen mode.
I create a launcher for all my remote Win servers and use the -g flag in order to force a specific size of the window. That way I can minimize or move it all I want, but still have a large screen.

This is how a typical MockY launcher looks like (the -0 flag is for logging in to a console session. Something that I recommend if you administrating the server or computer):

```
rdesktop -0 SERVERIP -u USERNAME -p PASSWORD - g 1270x975
```

---

### Post by Strawp on 2008-11-13
Yeah, I can set the size and have the window decoration but I actually want fullscreen but also the ability to switch desktop and have the TS client stick on the desktop I opened it on. I used to have this setup so that I had my local desktop on one side of the desktop cube and then one or two remote logins to Windows on another side of the cube. I can't seem to do this any more.

---

### Post by Peter09 on 2008-11-13
Does <CNTRL><ALTL><Right Arrow> turn the cube, or is it captured by the remote window?

---

### Post by Strawp on 2008-11-13
Yep, after ctrl+alt+enter, ctrl+alt+right does turn the cube, but the client window stays on top in fullscreen whereas in previous version it would stick to the desktop that it was opened on.

---

### Post by Peter09 on 2008-11-13
Compiz does have settings which determine whether a window appears on all faces of the cube, be worth checking how they are setup. I know after upgrading to Intrepid my Compiz settings changed in some areas.

These settings are also available for the window when you right click.

---

### Post by Strawp on 2008-11-13
Do you know where in the config those settings are?

---

### Post by Peter09 on 2008-11-13
See slight edit to my previous post. You can set this for individual windows by right clicking on the title bar.

Will check Compiz.

---

### Post by Strawp on 2008-11-13
Great, I'll try this out a bit later

---

### Post by Strawp on 2008-11-13
Tried it out - I can't set "only on this workspace" in the context menu of the window title bar because it's just full screen that I get the issue in. When it's not full screen it stays in the right desktop.

No idea where in the Compiz config I might find the option for this.

---

### Post by Strawp on 2008-11-18
No solution for this then? :(

Makes the Terminal Services Client considerably less usable if that is the case.

---

### Post by SimonHawkin on 2008-11-22
In 8.10 (Ibex), Ctrl-Alt-Enter worked just out of the box for me. However, YMMV.

---

### Post by Strawp on 2008-11-22
> **SimonHawkin said:**
> In 8.10 (Ibex), Ctrl-Alt-Enter worked just out of the box for me. However, YMMV.

Did it do a full minimise or did it just return the keyboard control to the Ubuntu desktop? If there's some setting I have in Compiz which is doing this, I'd quite like to find it.

---

### Post by eddo22 on 2008-12-04
i first had to install compizconfig settings manager in Synaptic, then run that and under Workarounds, disable Legacy Fullscreen Support.  After disabling, ctrl+alt+enter works like a charm for me.
hth,
ed

---

### Post by Strawp on 2008-12-04
> **eddo22 said:**
> i first had to install compizconfig settings manager in Synaptic, then run that and under Workarounds, disable Legacy Fullscreen Support.  After disabling, ctrl+alt+enter works like a charm for me.
hth,
ed

YES! Thank you, this works perfectly! :D

---

