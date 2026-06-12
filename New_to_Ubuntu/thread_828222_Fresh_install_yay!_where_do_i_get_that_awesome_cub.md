---
title: "Fresh install yay! where do i get that awesome cube?"
date: 2008-06-13
forum: New to Ubuntu
---

### Post by RedTooth on 2008-06-13
Compiz fusion or something? 

Were can i get the best and newest guide to installing that?

---

### Post by neurostu on 2008-06-13
google for "Advanced Desktop Effects Ubuntu"
"Desktop Cube, HOW TO, Ubuntu"

There are plenty of guides, google will find them!

---

### Post by burakerenn on 2008-06-13
If you have installed Hardy Heron you can activate directly from Apperance. Go to Visual Effects tab and make it Extra.

Then go to synaptic and install compizconfig-settings-manager. After you install it there'll be a option at Preferences > Advanced Desktop Effects, make them just what you like (like desktop cube etc.). Remember that you need at least 4 workspace and rotate cube option ticked for cube effect.

---

### Post by RomeReactor on 2008-06-13
Hi. Just to add to the comments, make sure you have at least a recent nVidia, ATI, or Intel video card; if your system uses another kind of integrated video (like VIA) it may be difficult, or in some cases downright impossible, to get the effects working.

Can you please post your system's specifications (video card, processor, amount of RAM?

---

### Post by wolfen69 on 2008-06-13
install your video card driver. reboot. then open the terminal and:


```
sudo apt-get install compizconfig-settings-manager
```

then go to system>preferences>appearance>visual effects and enable "extra". then go to system>preferences>advanced desktop effects settings to enable what effects you want.

here is a list of some of the things you can do

Desktop Effects1 Keyboard Shortcuts
Rotate Cube Mousewheel on Desktop
Switcher2 Alt + Tab
Shift Switcher3 Super + Tab (2 modes: flip and cover)
Ring Switcher Super + Tab - overrides Shift Switcher
Expo Super + E (toggle)
Film Effect Ctrl + Alt + Down Arrow4
Rotate Cube Manually Ctrl + Alt + Left Mouse Button
Scale Windows Alt + Shift + Up Arrow
Show/Clear Desktop Ctrl + Alt + D (toggle)
Snapping Windows Move a window across workspaces5
Screenshot Super + Left Mouse Button
Zoom In/Out Super + Mousewheel
Transparent Window Alt + Mousewheel
Resize Window Alt + F8
Move Window Alt + F7
Add Helper Super + P
Widget Layer F9 (toggle)
Water Effects Shift + F9 (toggle)
Fire Effects: On Super + Shift + Left Mouse Button
Fire Effects: Clear Super + Shift + C
Annotate: Draw Super + Left Mouse Button
Annotate: Start Super + 1
Annotate: End Super + 3
Group: Select Window(s) Super + S
Group: Group Windows Super + T
Group: Ungroup Windows Super + U
Group: Flip Windows Super + Right or Left Arrow

Make sure the effects are enabled to see results. You can do so by going to System - Preferences - Advanced Desktop Effects Settings. Some effects will disable others. For example, the Desktop Wall will disable the Desktop Cube, Snapping Windows will disable Wobbly Windows and many more. Please let me know if I missed something, so I can add more effects to the list.

---

### Post by phr0ze on 2008-06-13
I don't recommend googling for cube instructions. The cube has been around a while and the instructions have changed drastically between versions of ubuntu. I'd hate to see you stumble upon some archaic overly complicated instructions.

The steps mentioned above are exactly right. These days the hardest part with compiz (once you get past any compatability issues) is simply all the darn options and knowing how to set them.

---

### Post by fredunderhill on 2008-07-10
hey. i've seen videos of destop effects where people click on their applications tab and it flips down clockwise. how do i get it to do that?

---

### Post by crhylove on 2008-08-02
> **wolfen69 said:**
> install your video card driver. reboot. then open the terminal and:


```
sudo apt-get install compizconfig-settings-manager
```

then go to system>preferences>appearance>visual effects and enable "extra". then go to system>preferences>advanced desktop effects settings to enable what effects you want.

here is a list of some of the things you can do

Desktop Effects1 Keyboard Shortcuts
Rotate Cube Mousewheel on Desktop
Switcher2 Alt + Tab
Shift Switcher3 Super + Tab (2 modes: flip and cover)
Ring Switcher Super + Tab - overrides Shift Switcher
Expo Super + E (toggle)
Film Effect Ctrl + Alt + Down Arrow4
Rotate Cube Manually Ctrl + Alt + Left Mouse Button
Scale Windows Alt + Shift + Up Arrow
Show/Clear Desktop Ctrl + Alt + D (toggle)
Snapping Windows Move a window across workspaces5
Screenshot Super + Left Mouse Button
Zoom In/Out Super + Mousewheel
Transparent Window Alt + Mousewheel
Resize Window Alt + F8
Move Window Alt + F7
Add Helper Super + P
Widget Layer F9 (toggle)
Water Effects Shift + F9 (toggle)
Fire Effects: On Super + Shift + Left Mouse Button
Fire Effects: Clear Super + Shift + C
Annotate: Draw Super + Left Mouse Button
Annotate: Start Super + 1
Annotate: End Super + 3
Group: Select Window(s) Super + S
Group: Group Windows Super + T
Group: Ungroup Windows Super + U
Group: Flip Windows Super + Right or Left Arrow

Make sure the effects are enabled to see results. You can do so by going to System - Preferences - Advanced Desktop Effects Settings. Some effects will disable others. For example, the Desktop Wall will disable the Desktop Cube, Snapping Windows will disable Wobbly Windows and many more. Please let me know if I missed something, so I can add more effects to the list.

Hey, great little list, though I had a hard time telling exactly what your key commands were, or how to replicate them.  Please reformat them and add them to my list over here.  If you can Actually Pick the most important 10, that would be better for presentation.

Thanks again.  I learned a new one!
rhY

Here is the link to the brainstorm page:
[http://brainstorm.ubuntu.com/idea/11768/](http://brainstorm.ubuntu.com/idea/11768/)

---

### Post by jetta on 2008-08-06
Hi all, had some confusion here with the command in compiz manager, actually what does it mean by button 'Super'?

(sorry bad spelling maybe)

---

### Post by ConMan318 on 2008-08-06
If you are on a PC-type keyboard, it is the Windows button.

---

### Post by appi2012 on 2008-08-06
> **fredunderhill said:**
> hey. i've seen videos of destop effects where people click on their applications tab and it flips down clockwise. how do i get it to do that?

Open Advanced desktop effects. and go to the animation tab. Try changing the lines for the Open Effect. The line for the application tab is set by default to "fade" That might help you find it.

---

### Post by zuerston on 2009-06-15
How do you make the cube rotate with the mouse wheel? I have to click the icons in the bottom task bar to make it rotate.

---

### Post by jperez on 2009-06-15
BIG time necro, but to answer your question.

Normally, just press and hold Ctrl and then click your mouse on the desktop to start doing that.  If that doesn't work, you can configure it to do that under the Commands options in the Compiz manager.

I'm using KDE atm, so I can't tell you exactly what to use since it's been about a year or so since I've played around with Compiz/Beryl for Gnome.

Jesse~

---

