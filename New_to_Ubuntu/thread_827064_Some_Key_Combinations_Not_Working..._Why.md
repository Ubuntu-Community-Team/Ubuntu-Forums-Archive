---
title: "Some Key Combinations Not Working... Why?"
date: 2008-06-12
forum: New to Ubuntu
---

### Post by Xorxe on 2008-06-12
Hi, all. New to Linux, more or less, but not really new to computers. I was wondering if anyone could help me diagnose an interesting symptom that's cropped up on my laptop (An MSI, the model number escapes me at the moment, that was rebranded as a ZT, if that helps at all) running 8.04. 


Just today, after two reboots and two cold boots, some key combinations have ceased to work. Specifically, ALT-F4 doesn't close windows anymore. Some windows, if I hold the keys down for a very long time, eventually close, but this is not a general rule. ALT-F10 still maximizes instantly, ALT-F5 still unmaximizes, and ALT-F9 still minimizes. 

Also, in switching desktops (With whatever the default desktop switcher is), CTRL-ALT-UP has ceased switching to the desktop above- CTRL-ALT-DOWN still moves one desktop down, CTRL-ALT-LEFT/RIGHT to the appropriate directions, but not CTRL-ALT-UP. 

My first thought was that this might have something to do with Wine, which I have installed, but I have no idea how to check that. This is really starting to vex me, guys, please, please help.

Edit: Forgot to mention that, for the desktop switching issue, the mouse wheel still moves between desktops as appropriate. As well, when I reassign the keys, they work just fine with no problems (Right now I've switched "Move one Workspace Up" to CTRL-NumUp). Thanks.

---

### Post by neurostu on 2008-06-12
Did you install the advanced desktop effects? compiz-config-<something> try messing around with the key bindings in there

or If you didn't install it try System-->Preferences-->Keyboard Shortcuts
then just remap things to what you want.

---

### Post by Xorxe on 2008-06-13
Recent developments- and the fact that this sudden change in response has happened on THREE CLEAN INSTALLS NOW- tells me that either I'm installing some sort of wrong package, or there's something else afoot (FYI, despite both cores operating at 50%, the temperature on CPU, or so lm-sensors tells me, is just about 40 celsius- this might be normal, I have no idea, but damn does the laptop feel warm over the area that houses the processor heat sink.)

Other ideas I've had include blaming it on Wine, which I don't know how to disable without removing, and blaming it on Tellico-- which might be probable as reading the fine print it says that it's a KDE app. Could this have something to do with it? 

Either way, I know how to change the bindings, but I want the original ones to work! :( ALT-F4 and CTRL-ALT-UP are the only two that fail-- and I can get them to work if I hold them down for about ten seconds. 

Signed,
Confused N. Agitated.

---

### Post by Seth Kriticos on 2009-04-04
Thanks for the wine suggestion. I just had a similar problem, Shift+R/N/V stopped working. Did make a quick sudo apt-get purge wine and suddenly it worked again. I had the experimental wine packages running (wine 1.1.18 ).

---

