---
title: "Can't drag and drop to unity launcher"
date: 2011-08-11
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by CaptainMark on 2011-08-11
Im sure i could do in alpha 2 days, i seem to have lost the unity launchers drag and drop function, its a .desktop launcher im trying to drag but it just does nothing, can anyone confirm?


update: if i log out and log back into unity 2d i can drag and drop to the launcher correctly and the icon stays when i log back into unity 3d but doesnt function correctly, it basically doesnt repsond except to right click which brings the menu up but those options in turn still dont repsond, ill try another launcher to rule out a problem with that

---

### Post by terry_gardener on 2011-08-11
> **CaptainMark said:**
> Im sure i could do in alpha 2 days, i seem to have lost the unity launchers drag and drop function, its a .desktop launcher im trying to drag but it just does nothing, can anyone confirm?

yes i have the same problem

---

### Post by dino99 on 2011-08-11
i've some kind of similar issue with mouse settings way too much sensitive, and tweaking them via the dialog box dont change the problem. So dragging/expanding is a pain.

---

### Post by mc4man on 2011-08-11
That bug is fix committed, may be in the new unity today or so (4.8  - or may not
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/815045](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/815045)

---

### Post by x-shaney-x on 2011-08-11
Yes I can confirm that here.
Unity 2d still allows it and also accepts drag n drop from the lenses too.

It's odd, 2d seems way ahead of 3d in certain things and way behind in others.
Hopefully they should meet somewhere in the middle come October 10th :)

---

### Post by CaptainMark on 2011-08-11
yeah it worked in natty, i hate regressions,

---

### Post by mc4man on 2011-08-11
Well the D&D and launcher shortcuts have been fixed and are now working in unity 4.8

(can't say anything good about  the new big, ugly, red button, dash blur and unity panel

---

### Post by cejack on 2011-08-29
Well you can drag and drop but I can't figure out how to get it from changing back to the ugly / non-specific springboard launcher icon once it copies over to Unity launcher bar...

---

### Post by mc4man on 2011-08-29
> **cejack said:**
> Well you can drag and drop but I can't figure out how to get it from changing back to the ugly / non-specific springboard launcher icon once it copies over to Unity launcher bar...

What you're dragging is a .desktop file. So open it up either thru it's properties or in a text editor and fix (Icon= line in a text editor

---

### Post by cejack on 2011-08-29
Well, it's a file from "/.local/share/applications" that is dragged and dropped onto the Unity file launcher.  

I can drag it to the desktop from Nautilus window and it's fine and retains its icon.  

I drag it from Nautilus to the Unity Launcher and it works but the icon gets hosed and looks like this:

[ATTACH]201075[/ATTACH]

I drag it from the Desktop to the Unity Launcher and I just get a blank button area on the Unity Launcher bar.  That's obviously a problem as well. 

Regardless of what you do, the icon gets corrupted or screwed up or whatever you want to call it when it gets dropped on the Unity Launcher bar.  (Not sure why this is happening - ergo my post and many others...)  

Nowhere is there a *.desktop extension on the file that I can see in Nautilus.  I can check in Terminal.  

All I can say is this is way too difficult for what should be a simple task.  This works seamlessly on MACS and on Windows.  It also worked great with Cairo Dock under all previous Linux distros I've used.  Monkeys could drop icons to the Launch Bar / Task Bar on those OS's. 

(Drag and drop of program icons probably still does work great with Cairo Dock but I'm trying to give this Unity thing a try.  Have not been real impressed with it and it seems awful buggy to me if you can't simply create your own launchers and drag them to the Unity launch bar without some kind of error.)

---

### Post by mc4man on 2011-08-29
If you wish - open a text edit, then drag & drop the file from "/.local/share/applications" into the editor.
Post what shows, maybe something can be adjusted

---

### Post by cejack on 2011-08-29
All right.  So I just had some time to try it again.  

I did sudo gedit "whateverfile" in the "/.local/share/applications" folder.  

Went and copied and pasted in an icon name into the "Icon=" section of the file when opened in Gedit.  The Icon was from "usr/share/icons" after hunting around on-line where Ubuntu defaults the icon files to.

Whatever this technique solves this seemed to work.  (I confess I   know not why this works...  Anybody that knows feel free to elucidate.  I suspect there is some security thing at play here.) 

Perhaps has something to do with permissions.  Perhaps one has to drag and drop icons only from a sudo or gksudo nautilus command or something.  I would imagine there was some kind of permissions on the icons or something that was creating a problem.

All I'm saying is this is just totally confusing to folks that are transitioning from other OS's.  I use everything (Windows, Mac, Linux) just because some tools are better than others on their respective platforms.  

At a minimum, if it's a security problem to take icons from the "usr/share/icons" location then it should deny you completely when you browse or drag and drop an icon on the launcher.  Or it should ask you to supply administrative password privileges if this is a perceived security risk that can be solved by requiring a system admin password.  (Not sure what an icon image could do with security unless there's like a porno icon gag package out there some guy could put on Granny's computer or something...)  

The problem I see is that the OS let's you do this (plop an icon in the program launcher or browse to an icon) and it actually works in a folder or on the desktop.  But it still hoses your icon when you try and plop it on the Unity Launcher.  (I am curious why the terminal command I added to this launcher still worked with the bad icon...)  

Anyhow, I solved the problem by taking your advice.  (Thanks...!)  It appears that if you do as you suggest in a text editor with a valid file location and valid file name with sudo / root privileges, you'll be OK after saving your file edit and then dragging your newly edited launcher file with icon to the Unity Launcher bar.  But it's certainly not very intuitive or easy for a beginner to handle.  I'd consider myself a mid-level Ubuntu user just because I've used it since 8.04 and know enough rudimentary commands and tasks to be dangerous.  (No guru here.) 

But it is definitely confusing and frustrating.  Perhaps this is an issue that the most unsophisticated and rudimentary users will not encounter because they will never bother making their own program launchers. 

There is one thing I think is great about the newer kernels out there, especially Ubuntu 11.04.   They have definitely got multi-boot down to a science that is very reliable with Grub2.  Very good and simple to handle and I've installed on a bunch of machines in dual boot configuration with Windows or old Linux installs and have yet to have a problem.  Good job there...

---

