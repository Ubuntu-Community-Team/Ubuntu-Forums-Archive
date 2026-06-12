---
title: "changing power button shut off characteristics"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by thebestofall007 on 2008-04-29
hello, i have just upgraded to hardy heron and had that sound bug that muted the audio from audio/videos when firefox played a flash video and fixed that, in part following the thread 

http:/ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive+sound+guide

and getting the libflashsupport package installed.

i reinstalled the alsa sound packages and also had to install gdm and ubuntu-desktop packages to keep my desktop intact as the thread instructed. unfortunately, this changed what my power button does when pressed. before i had the sound issue, i would press the button and the computer would ask me what i wanted to do (hibernate, shut down, restart, log off, lock screen). now it immediately logs off and goes to the login screen. i went to the power management menu and chose the "ask me" option when i pushed the power button (like i had it). no-go.
 
 HOW DO I CHANGE IT BACK THE WAY IT WAS (back to where the menu comes up when i press the power button)?

---

### Post by Vadi on 2008-05-01
Try right-clicking on the quit icon, and then 'remove from panel'. Then right-click on the icon, add to panel, search for "quit", and add the "Quit..." applet. See if that helps?

---

### Post by Gepetto on 2008-05-01
Check
System->preferances->power management->general

And make sure the setting is set to "ask me"

---

### Post by thebestofall007 on 2008-05-03
> **Gepetto said:**
> Check
System->preferances->power management->general

And make sure the setting is set to "ask me"

i have, but the problem still persists.

---

