---
title: "Care to help a misrable noob?"
date: 2008-06-07
forum: New to Ubuntu
---

### Post by RedTooth on 2008-06-07
I just got ubuntu and i am wondering how i can install Compiz fusion and the cool cube and fire effects and all... Hehe


Please help me

---

### Post by wolfen69 on 2008-06-07
compiz is already installed. go to system>admin>hardware drivers. install your video card driver. reboot. then open the terminal and
```
sudo apt-get install compizconfig-settings-manager
```
then go to system>preferences>appearance>visual effects and enable "extra". then go to system>preferences>advanced desktop effects settings to enable what effects you want.

here is a list of some of the things you can do

Desktop Effects1 	Keyboard Shortcuts
Rotate Cube 	        Mousewheel on Desktop
Switcher2 	        Alt + Tab
Shift Switcher3 	Super + Tab (2 modes: flip and cover)
Ring Switcher 	        Super + Tab - overrides Shift Switcher
Expo 	                Super + E (toggle)
Film Effect 	        Ctrl + Alt + Down Arrow4
Rotate Cube Manually 	Ctrl + Alt + Left Mouse Button
Scale Windows 	        Alt +  Shift + Up Arrow
Show/Clear Desktop 	Ctrl + Alt + D (toggle)
Snapping Windows 	Move a window across workspaces5
Screenshot 	        Super + Left Mouse Button
Zoom In/Out 	        Super + Mousewheel
Transparent Window 	Alt + Mousewheel
Resize Window 	        Alt + F8
Move Window 	        Alt + F7
Add Helper 	        Super + P
Widget Layer 	        F9 (toggle)
Water Effects 	        Shift + F9 (toggle)
Fire Effects: On 	Super + Shift + Left Mouse Button
Fire Effects: Clear 	Super + Shift + C
Annotate: Draw 	        Super + Left Mouse Button
Annotate: Start 	Super + 1
Annotate: End 	        Super + 3
Group: Select Window(s) Super + S
Group: Group Windows 	Super + T
Group: Ungroup Windows 	Super + U
Group: Flip Windows 	Super + Right or Left Arrow


Make sure the effects are enabled to see results. You can do so by going to System - Preferences - Advanced Desktop Effects Settings. Some effects will disable others. For example, the Desktop Wall will disable the Desktop Cube, Snapping Windows will disable Wobbly Windows and many more. Please let me know if I missed something, so I can add more effects to the list.

---

### Post by bumanie on 2008-06-07
Follow this [http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion](http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion)

---

### Post by django0909 on 2008-06-07
It might be worth noting that not everyones graphics hardware setup will work with fusion. Use Compiz-Check, (google it), to see if it does.

---

### Post by RedTooth on 2008-06-07
I typed the command you gave me into the terminal and it told me this..



E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

### Post by Zebra Lord on 2008-06-07
I just figured out how to do this two minutes ago

go to System > Administration > Synaptic Package Manager

then use search to look for "compizconfig-settings-manager" 

check the manager and then click apply and it should start downloading

after it is installed go to this website for help configuring the effects:

[http://forlong.blogage.de/article/2008/4/26/How-to-set-up-Compiz-Fusion-074](http://forlong.blogage.de/article/2008/4/26/How-to-set-up-Compiz-Fusion-074)

hope this helps

i am still configuring the updates and they are sooooooooooo cool

---

### Post by wolfen69 on 2008-06-07
do ctrl-alt-backspace and log back in, and then try it.

---

### Post by Forlong on 2008-06-07
> **RedTooth said:**
> I typed the command you gave me into the terminal and it told me this..



E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
That simply means you are running Synaptic (or the Add/Remove tool) and trying to install something via command line at the same time.

You have to close the graphical one to make it work.

---

