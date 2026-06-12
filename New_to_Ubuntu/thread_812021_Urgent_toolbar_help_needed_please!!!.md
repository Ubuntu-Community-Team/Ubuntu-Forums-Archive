---
title: "Urgent toolbar help needed please!!!"
date: 2008-05-29
forum: New to Ubuntu
---

### Post by steve63 on 2008-05-29
Hi All,
Am just getting used to using Ubuntu 8 and loving it when I turned my machine on and the main toolbar is missing, the one with applications, system, time, date, etc on it. I rebooted twice and tried booting with recovery mode too but its still not there. I can still access a lot of programs as I installed the mac lookalike toolbbar (ADF or something??) and thats still there. How do I get the toolbar back please,thanks for any advice.
Steve.

---

### Post by mmb1 on 2008-05-29
try pressing alt-f2 and typing in "gnome-panel".

---

### Post by steve63 on 2008-05-29
Hi,
Thanks for that but when I press alt & f2 nothing happens, nothing opens or anything???
Steve

---

### Post by mmb1 on 2008-05-29
Are you pressing them both at the same time, a box should appear that says "run Application"  If it doesn't work this time, do you have access to a terminal?  If so try running "gnome-panel" there.

---

### Post by steve63 on 2008-05-29
Hi again, yep pressing them both together and nothing happens. Is it possible to open a terminal without going via the applications/terminal route for which I need the toolbar???
Steve

---

### Post by harsh1kumar on 2008-05-29
Do you have the pannel at the bottom of the screen, which shows the opened windows. 
Right click on it. 
Click New panel.
drag to the place you want it. 
Right click on it.
click add to panel.
Add the 'main menu' or custom menu option from it. 
All other buttons present default can be added from this window.

---

### Post by steve63 on 2008-05-29
Hi no panel and if I didnt have the mac lookalike toolbar I'd have a blank desktop.
Steve

---

### Post by mmb1 on 2008-05-29
What do you have access to via your dock?

---

### Post by Steve90210 on 2008-06-19
I have the exact same problem. No upper toolbar or bottom tool bar.

---

### Post by Steve90210 on 2008-06-19
Okay, so I opened terminal and typed in 'gnome-panel'.

It said something about it not being installed and gave me the sudo code to use if I want to install it. So, I typed that sudo code and hit enter, then typed in my password for sudo. It downloaded and installed the program. Then I hit ctrl-alt-delete and logged out. When I logged back in, the bars are back, but I have three error prompts

> The panel encountered a problem while loading "OAFIID:GNOME_FastUserSwitchApplet".

Do you want to delete the applet from your configuration?

Don't Delete              Delete

The other two prompts are for OAFIID:GNOME_Panel_TrashApplet and OAFIID:GNOME_MixerApplet.

I just deleted Fast_UserSwitch because this is my laptop and I only have one user and therefore never liked having that icon up there anyway. I'd like the trash applet to work though. Anyone know what I have to do to fix it? 

Not sure what the mixer applet is. Maybe it was for the audio volume control? Because that one is still missing.



I think this whole problem came about when I uninstalled evolution mail last night. I tried doing it from Add/Remove, but it said that removing it would affect other programs and that I'd have to use Synaptic Package Manager. I think the toolbar was one of those things that was affected.

---

### Post by cariboo on 2008-06-19
Evolution is a core part of Ubuntu if you uninstall it a lot of other applications you need will uninstalled also. In a terminal type:

```
sudo apt-get install ubuntu-desktop
```

That should solve your problem.

Jim

---

### Post by Steve90210 on 2008-06-19
> **cariboo907 said:**
> Evolution is a core part of Ubuntu if you uninstall it a lot of other applications you need will uninstalled also. In a terminal type:

```
sudo apt-get install ubuntu-desktop
```

That should solve your problem.

Jim
That worked. Thank you.

---

