---
title: "OzOs Issue"
date: 2008-02-26
forum: Other OS Talk
---

### Post by ErusGuleilmus on 2008-02-26
I recently installed OzOs. It pretty much worked perfectly out of the box, with the exception of the animations and effects. For example, when I double click on the desktop, it brings up the (for lack of a better term) "start menu". The menu itself appears immediately. But when I scroll over the different options, there is a one second lag between the cursor crossing over an item and it actually highlighting. Because I could not find the Restricted Drivers Manager (I believe that Oz is Ubuntu based), I installed the Nvidia drivers via Synaptic. I assume that when I installed and rebooted, that the new driver would be the one being used. If it did install, it had no effect on the preformance of the effects. What can I do to rectify this? Thank you for putting up with my poorly written plea for help.

Erus

---

### Post by Rui Pais on 2008-02-29
> **ErusGuleilmus said:**
> I recently installed OzOs. It pretty much worked perfectly out of the box, with the exception of the animations and effects. For example, when I double click on the desktop, it brings up the (for lack of a better term) "start menu". The menu itself appears immediately. But when I scroll over the different options, there is a one second lag between the cursor crossing over an item and it actually highlighting. Because I could not find the Restricted Drivers Manager (I believe that Oz is Ubuntu based), I installed the Nvidia drivers via Synaptic. I assume that when I installed and rebooted, that the new driver would be the one being used. If it did install, it had no effect on the preformance of the effects. What can I do to rectify this? Thank you for putting up with my poorly written plea for help.

Erus

Hi Erus,
sorry this late answer (for faster replies always post on OzOS thread). 

Thanks for your interest on Oz OS!

About the menu issues. Thats usually a bug with certain .desktop files that seems to contain any incorrect config that works normally on gnome but make e17 menus redraw frooze by a second...
But that shouldn't happen on a out-of-the-box OzOS. 
Have you installed any other software?

About restricted-manager, it's installed by default but (again) the .desktop file don't appears on standard e17 menu (i will have to yune this on next release... )
You can run it from terminal or from 'Run' comand (Alt+Esc) :
```
restricted-manager
```
I recommend you give an eye on [Envy]("http://albertomilone.com/nvidia_scripts1.html"), that seems to work better and install more updated drivers.
Note that i doubt it will solve the issue with menus (you need to find the bad behavior menu entry...)

To ensure that you are using nvidia driver type:
```
cat /etc/X11/xorg.conf | grep nvidia
```
and 
```
lsmod | grep nvidia
```
on a terminal and if outputs something it indicates:
of 1st instruction, X server it's configured to use nvidia driver (instead of nv)
of 2nd instruction, nvidia driver it's loaded.

If some of those commands outputs nothing, that means that it's not correctly configured and/or loaded.

---

