---
title: "ASUS - 10.04 and brightness control"
date: 2012-01-30
forum: New to Ubuntu
---

### Post by casondave on 2012-01-30
Hi Folks,
 
I have a ASUS EeePC that's been upgraded from 9.04 to 10.04 LTS and there is a problem with the LCD brightness settings.  The hotkeys on the laptop don't happilly run the brightness. :(
 
I was using the command: sudo setpci -s 00.02.0 F4.B= xx 
( where xx is the set to 70% for batt and 99 % for plugged in )
 
Now when I type it in I get back:  setpci -s: Invalid function number
 
It used to work!  Any suggestions?  
 
 
When I run lspci I get back:  00.02.0 VGA compatble controller; Intel Corp N10 Family Intergrated Graphics Controller so I'm on the right page for the laptop!
 
Cheers'
Dave

---

### Post by Michael Dooley on 2012-01-30
Try adding the "Brightness Applet" to Gnome panel. Right click on panel, select 'add to panel', you should see the applet.

---

