---
title: "[SOLVED] Desktop workspaces broken after update"
date: 2008-10-10
forum: New to Ubuntu
---

### Post by DoubleMcLovin on 2008-10-10
[COLOR="Red"]SOLVED[/COLOR]

so I was performing the update through the update manager, and it hung while in the "cleaning up" stage. The terminal reported it was doing something to a python file for about an hour before I went ahead and rebooted the computer. After it started the desktop workspaces (the screens that I can select a different desktop session using them located in the bottom right) no longer respond, and also ALT+TAB doesn't respond. Those are the only 2 bugs I noticed right away. I tried running the update manager again to no success.

[COLOR="Red"]EDIT:[/COLOR]
Ok, so I looked into the "System-->Preferences-->Keyboard Shortcuts" and ALT+TAB is still configured to switch desktops, but still doesn't work. And I tried pressing CTRL+ALT+RIGHT/LEFT to switch to my other desktops, and I received a "BEEP" from my computer like I was putting in an invalid command. =[ I can still move windows to the other desktops and they show up in the display on the bottom right, but I am unable to access them after that and have to kill the process and relaunch to get to it.

---

### Post by Joeb454 on 2008-10-10
Did the update manager give any errors etc.?

---

### Post by DoubleMcLovin on 2008-10-10
nope, none. It just hung. I tried breaking the command using CTRL+C before I reset the PC and it didn't do anything.

---

### Post by DoubleMcLovin on 2008-10-10
bump

---

### Post by DoubleMcLovin on 2008-10-12
I really hate to bump twice, but even if someone just knew the name of the process or program/script that is running the desktop switching thing that might help me. Google is no help cause I have no idea what to call that thing. =[ I miss having more then 1 desktop, it was so much more efficient.

---

### Post by drs305 on 2008-10-12
Metacity has a setting to set the number of workspaces. Open gconf-editor in terminal and go to /apps/metacity/general/num_workspaces  When I change the value the number of desktops/workspaces immediate changes (the lower right windows change). 

The keybindings for swapping workspaces in gconf are in /apps/metacity/global_keybindings/

Metacity is in synaptic. It wouldn't hurt to reinstall it.

Unfortunately I don't know the commands they invoke, but you might just make sure those settings still are set.

---

### Post by DoubleMcLovin on 2008-10-13
Well, I reinstalled Metacity, didn't work even after restart. So I reinstalled the packages installed that came with it, restarted and still didn't work. I found it interesting that there wasn't a /apps/metacity/general/num_workspaces file present. I saw some others, including the global keybindings (keybindings were set) one, but that one was missing.

---

### Post by drs305 on 2008-10-13
> **DoubleMcLovin said:**
> I found it interesting that there wasn't a /apps/metacity/general/num_workspaces file present. I saw some others, including the global keybindings (keybindings were set) one, but that one was missing.

I don't know if it will help, but you can create that key in /apps/metacity/general by right clicking in the right window, Add Key,
Name: num_workspaces
Type: integer
Value: enter digit  (4 is mine)

---

### Post by DoubleMcLovin on 2008-10-14
That didn't work for me either =\, but I did have some success elsewhere. After some google-ing thanks to knowing the name of metacity I think I tracked down the problem, I re-installed compiz (*all installed packages) and installed the package "compiz" which was not installed. Rebooted and no success, I tried opening a terminal and typing in "compiz" then hitting enter and everything worked great!! So this leads me to believe that compiz is not set to run at boot, how can I add it to where it is?

EDIT:
I also noticed now that I dont have a close, minimize or maximize button on the top of my windows, and that my windows cover the top bar in gnome by default =\ something with the theme getting broken as a result of compiz maybe?

EDIT2: Wooo, I got compiz to run at startup by going into "System-->Preferences-->Sessions" and adding an entry to run "compiz" there; this also fixed my theme problems. Restarted and it worked fine the SECOND reboot. Interestingly enough, now when I click preferences on the windows in the bottom right, I have the option to name them instead of manually naming them in gconf =D

[COLOR="Red"]THIS TOPIC IS SOLVED[/COLOR]

---

